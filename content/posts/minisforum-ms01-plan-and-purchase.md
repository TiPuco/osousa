---
title: "Building the Next Homelab Node: The Minisforum MS-01 Plan"
date: 2026-08-05
draft: false
tags: [homelab, networking, proxmox, minisforum]
summary: "Planning notes on a new Proxmox node built around the Minisforum MS-01 — hardware, topology, storage layout, and why I consolidated the order with a 10G switch upgrade. Parcel's still in transit."
---

## Why This Build

My homelab has been running on a patchwork of small boxes for a while now — a Raspberry Pi 3 doing double duty as the UniFi Controller, a Mac Studio carrying more workloads than it probably should, and no dedicated place to actually test things without touching production services at home. It works, but it's reached the point where "just one more container" isn't really an option anymore.

The plan is to bring in a dedicated Proxmox node — something with real CPU headroom, proper multi-NIC networking, and enough storage tiers to separate boot, VM data, and cold storage cleanly. That also frees up the Pi3 for something more focused: acting as a Tailscale subnet router and a Chrony NTP server for off-site backup sync, rather than being stretched thin running the UniFi Controller on top of everything else.

## Hardware Chosen — and Why

After going back and forth on a few mini-PC and NUC-class options, I landed on the **Minisforum MS-01**: i9-13900H, 64GB RAM. It's a compact box, but the CPU headroom and the fact that it actually exposes proper 10G networking (rather than needing an add-in card crammed into a tiny chassis) made it the clear pick over the alternatives I was considering.

Since I was already placing an order through my typical US freight forwarder (Stackry), it made sense to consolidate rather than pay for shipping twice. So the same shipment includes:

- A **MikroTik CRS304-4XG-IN** — a 4-port 10G switch, which becomes the new backbone for the homelab segment
- A **10Gtek SFP+ → RJ45 10GBase-T module**, to bridge the MS-01 into the switch over standard copper
- A **10Gtek SFP → RJ45 2.5G module**, for the existing MikroTik L009 router

Bundling all three into one freight consignment cut down on shipping overhead and meant the whole networking upgrade and the compute upgrade could land — and get built — at the same time, rather than in disconnected stages.

## Planned Topology

The rough plan for how everything connects:

- **Mac Studio → CRS304**, via a new Cat6 run — the existing copper run to the Mac Studio stays on the Netgear 1Gbps switch feeding the streamer, so this will be a fresh cable pulled alongside it, not a repurposed connection
- **MS-01 → CRS304**, via the 10G SFP+ module
- **MikroTik L009 → CRS304**, via the 2.5G SFP module

The CRS304 becomes the central 10G switch tying the Mac Studio, the new Proxmox node, and the existing router together — replacing what was previously a much slower bottleneck between these devices.

## Storage Plan

Storage layout is split by purpose rather than just "biggest drive gets the most":

- **256GB PM961** — dedicated Proxmox boot drive, nothing else on it
- **1TB NVMe** — primary VM datastore, where the actual workloads live
- **Samsung 970 Pro 512GB** — secondary VM datastore / overflow
- **OWC 4M2 enclosure** — reserved strictly for ISOs, backups, and cold storage — deliberately kept separate from anything performance-sensitive

Keeping the boot drive isolated from the VM datastore is a small thing, but it avoids the classic homelab mistake of everything sharing one disk and one failure domain.

## What's Still Being Evaluated

A couple of things are still open questions rather than finalized decisions:

- **Repurposing the Pi3** as a Tailscale subnet router and Chrony NTP server, once the UniFi Controller migrates off it and onto the new node (likely as an LXC container)
- **Whether to run Windows Server on this node at all** — mainly to have a proper environment for security testing and research, rather than any production need. Still weighing whether that's worth the resource overhead versus just keeping the node Linux/Proxmox-focused

Neither of these is locked in yet — they'll get sorted out once the actual build starts.

## Current Status

As of writing this, the parcel is still in transit — latest DHL update has it arriving at the New York City Gateway sort facility yesterday at 09:19. Nothing has actually landed here yet — this post is entirely the plan, not the build.

Next up: unboxing once DHL delivers.
