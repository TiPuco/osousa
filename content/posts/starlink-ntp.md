---
title: "Your Starlink Dish is a Stratum 1 NTP Server — And Most People Don't Know It"
date: 2026-06-14
draft: false
tags: ["networking", "homelab", "starlink", "ntp", "infrastructure"]
description: "Starlink quietly added a GPS-based NTP server to every dish. Here's what that means, why it matters, and how to put it to work on your home network."
cover:
    image: "img/starlink-ntp.jpg"
    alt: "Starlink dish as a Stratum 1 NTP server"
    relative: false
---

I stumbled across something genuinely useful while setting up a local NTP server for my home network: Starlink quietly added a GPS-based NTP server to every dish, accessible locally at a fixed IP address. It's been there since mid-2024, it's officially documented, and almost nobody is using it.

Here's what that means, why it matters, and how I put it to work.

---

## What Is NTP and Why Should You Care

Network Time Protocol (NTP) is how computers agree on what time it is. This sounds trivial until you realise how many things depend on accurate time — TLS certificate validation, log correlation, authentication tokens, scheduled tasks, database transactions. When clocks drift, things break in subtle and maddening ways.

Most devices sync their clocks automatically from internet time servers. For the average home network this is fine. But if you're running infrastructure — servers, firewalls, containers, anything that generates logs you might want to correlate — having a reliable, low-latency, local time source matters.

**NTP uses a stratum system** to indicate how close a clock source is to a reference standard. Stratum 0 is the atomic clock or GPS receiver itself. Stratum 1 is a server directly connected to a Stratum 0 source. Stratum 2 syncs from Stratum 1, and so on. The lower the stratum, the more authoritative and accurate the time.

Most public NTP servers on the internet are Stratum 2 or 3. Getting Stratum 1 time typically requires either expensive GPS hardware or access to a university or national standards laboratory.

---

## The Starlink Discovery

Starlink's dishes contain GPS receivers — this is fundamental to how the system works. The satellites use precise timing to coordinate their low-earth-orbit network, and the dish knows exactly what time it is to a very high degree of accuracy.

What Starlink did in mid-2024 is expose that GPS clock as an NTP server on the local network. According to their official support documentation:

> *"Each Starlink runs an NTP server based on GPS time. The time is based on GPS; however, we cannot guarantee accuracy as the service is provided on a best-effort basis."*

The "best-effort" caveat is standard legal hedging. In practice, GPS-derived time is extremely accurate — accurate enough to be classified as Stratum 1. When I pointed my NTP client at the dish, it connected immediately and reported sub-millisecond offset from reference time.

The implication: anyone with a Starlink dish already has a Stratum 1 time source sitting on their local network. They just don't know it.

---

## The Implementation

My home network runs a Raspberry Pi 3B as an infrastructure host — it handles a few local services and sits on a dedicated management VLAN isolated from general network traffic. This made it the obvious place to run a local NTP server using **chrony**, one of the best NTP implementations available for Linux.

The setup has three layers:

**Layer 1 — Chrony on the Pi syncs from the Starlink dish.** The dish responds at Stratum 1. Chrony connects to it as the preferred source, with public internet NTP pools configured as fallbacks in case the dish is unreachable or the Starlink link is down. Chrony's clock discipline algorithm handles the occasional Starlink latency spikes gracefully, smoothing out any jitter before it affects downstream clients.

**Layer 2 — The Pi serves NTP to the local network.** Chrony listens for NTP queries from trusted subnets and responds as a Stratum 2 server. Every device on the trusted network gets GPS-derived time with a single local network hop of latency — typically under 2ms.

**Layer 3 — The router distributes the NTP server address via DHCP.** RouterOS supports advertising a custom NTP server address as a DHCP option. When a device joins the network and gets an IP address, it also gets told where to find the local NTP server. No manual configuration required on client devices.

The result: every trusted device on the network syncs from a GPS clock, through a local server with ~1ms latency, with multiple internet fallbacks for resilience. The Pi reports time offset from the Starlink dish at under a millisecond. Downstream clients report offset from the Pi at similarly tight margins.

---

## Why Not Just Use Internet NTP

Fair question. For most use cases, internet NTP is perfectly adequate. But there are a few reasons the local approach is better for a home infrastructure setup:

**Latency and accuracy.** Internet NTP pools introduce variable round-trip times — tens to hundreds of milliseconds. Chrony compensates for this, but a local server with consistent sub-2ms latency produces more stable and accurate synchronisation.

**Resilience.** If your WAN link goes down, devices that rely solely on internet NTP will eventually drift. A local NTP server with chrony's holdover capability continues serving accurate time for hours after losing internet connectivity, using its disciplined local clock. For a network infrastructure device like a router or firewall, this matters.

**Independence from external services.** This fits a broader philosophy of reducing dependency on external services for core infrastructure functions. DNS runs locally. The network controller runs locally. Time should too.

**Security.** NTP amplification attacks are a real thing. Devices querying internet NTP servers over a public WAN are marginally more exposed than devices querying a local server. It's a small benefit, but it costs nothing.

---

## The Chrony Advantage

I chose chrony over the more familiar ntpd for a few reasons. Chrony was designed specifically for environments with intermittent or variable-latency network connections — exactly what Starlink is. It handles large initial clock offsets gracefully, converges faster after network interruptions, and uses a more sophisticated clock discipline algorithm that produces tighter synchronisation over time.

On a Pi 3B with minimal load, chrony consumes essentially no resources. It's been running continuously without issue.

---

## A Detail Worth Noting

The Starlink dish is only reachable on the local network via its fixed management IP. If you're running a third-party router in bypass mode — as many homelab users do — you may need to verify that this address is reachable from your LAN before configuring it as an NTP source. A simple ping test will confirm connectivity before you change any configuration - mine is in bypass mode and responded to the ping.

---

## The Takeaway

If you have Starlink and you're running any kind of home server or infrastructure, you have a free Stratum 1 GPS time source already installed on your roof. It takes about twenty minutes to set up chrony on a local server and point it at the dish. The result is a GPS-accurate time infrastructure for your entire network that operates independently of the internet.

It's one of those small infrastructure details that nobody notices when it's working and everyone notices when it isn't. Worth twenty minutes of your time.

---

*Osvaldo de Sousa is a cybersecurity analyst based in Maputo, Mozambique. This post is part of an ongoing series on home infrastructure and security.*