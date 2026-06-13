---
title: "Hi-Fi"
layout: "single"
url: "/hifi/"
summary: "Osvaldo Sousa's Hi-Fi system"
---

Music is serious business here. This page documents the system I've built over the years — sources, amplification, speakers, cables, and the network infrastructure that ties it all together.

---

## Signal Chain

Intel NUC (Roon ROCK)

↓

Mac Studio M1 Ultra (as Roon endpoint or directly for video) or Holo Audio RED (DDC/Streamer) (Roon endpoint)

↓

Holo Audio Cyan 2 (DAC)

↓

Naim NAC 282 powered by TeddyCap SE + NAPSC

↓

Naim NAP 250DR

↓

Dynaudio Heritage Special + Pair of REL S/510


---

## Speakers

<img src="/img/hifi-speakers.jpg" alt="Dynaudio Heritage Special" style="width:100%; border-radius:8px; margin-bottom:1rem;">

| Component | Details | Link |
|---|---|---|
| **Loudspeakers** | Dynaudio Heritage Special · Limited edition · Pair 0521 of 2500 · IsoAcoustics Gaia 3 | [Dynaudio](https://dynaudio.com/home-audio/heritage-collection/heritage-special) |

---

## Subwoofers

<img src="/img/hifi-rel.jpg" alt="REL S/510 Subwoofer" style="width:100%; border-radius:8px; margin-bottom:1rem;">

| Component | Details | Link |
|---|---|---|
| **Subwoofers** | REL S/510 × 2 · High-level Neutrik Speakon input | [REL](https://rel.net/product/s-510/) |

---

## DAC & Streamer

<img src="/img/hifi-cyan2-red.jpg" alt="Holo Audio Cyan 2 and RED" style="width:100%; border-radius:8px; margin-bottom:0.5rem;">
<img src="/img/hifi-red.jpg" alt="Holo Audio RED DDC Streamer" style="width:100%; border-radius:8px; margin-bottom:1rem;">

| Component | Details | Link |
|---|---|---|
| **DAC** | Holo Audio Cyan 2 · R2R discrete ladder · DSD1024 · NOS | [Kitsune HiFi](https://kitsunehifi.com/products/holo-audio-cyan-2-dac-us) |
| **DDC & Streamer** | Holo Audio RED · Roon Ready · DSD512 · I2S/SPDIF/AES/BNC output | [Kitsune HiFi](https://kitsunehifi.com/products/holoaudio-red-ddc-network-streamer-1) |

---

## Amplification

<img src="/img/hifi-nac282.jpg" alt="Naim NAC 282 Preamplifier" style="width:100%; border-radius:8px; margin-bottom:0.5rem;">
<img src="/img/hifi-napsc-teddycap.jpg" alt="NAPSC and TeddyCap SE" style="width:100%; border-radius:8px; margin-bottom:0.5rem;">
<img src="/img/hifi-nap250.jpg" alt="Naim NAP 250DR Power Amplifier" style="width:100%; border-radius:8px; margin-bottom:1rem;">

| Component | Details | Link |
|---|---|---|
| **Preamplifier** | Naim NAC 282 | [Naim Audio](https://www.naimaudio.com/products/nac-282) |
| **Preamp PSU** | TeddyCap SE + NAPSC | [Teddy Pardo](https://teddypardo.com/product/teddycap-se/) |
| **Power Amplifier** | Naim NAP 250DR | [Naim Audio](https://www.naimaudio.com/products/nap-250-dr) |

---

## Source & Digital

| Component | Details | Link |
|---|---|---|
| **Roon Core** | Intel NUC running Roon ROCK · 4TB Samsung SSD on OWC Express 1M2 USB4 enclosure | [OWC Enclosure](https://www.bhphotovideo.com/c/product/1801760-REG/owc_owcus4exp1m2_express_1m2_portable_nvme) |
| **DDC & Streamer** | Holo Audio RED · Roon Ready · DSD512 · I2S/SPDIF/AES output | [Kitsune HiFi](https://kitsunehifi.com/products/holoaudio-red-ddc-network-streamer-1) |
| **Roon Endpoint** | Mac Studio M1 Ultra via USB | [Apple](https://www.apple.com/mac-studio/) |

---

## Cables

| Connection | Cable |
|---|---|
| Mac Studio → DAC | [Wireworld Ultraviolet 8 USB A to B](https://www.amazon.com/s?k=wireworld+ultraviolet+8+usb) |
| Streamer → DAC | [Mogami 2964 Digital Coaxial 75Ω BNC](https://www.amazon.com/dp/B079J1QMBJ) |
| DAC → Preamp | [CHC Blue RCA to DIN](https://www.custom-hifi-cables.co.uk/audio-interconnects/midnight-range/blue-din-rca-rca-din) |
| Preamp → Amp | [CHC Blue DIN to 250 XLR](https://www.custom-hifi-cables.co.uk/audio-interconnects/midnight-range/blue-din-xlr) |
| Amp → Speakers | Witch Hat Phantom 6m · Bananas/Bananas *(company closed)* |
| Speakers → Subs | [Van Damme · Neutrik to Spades](https://www.ebay.com/itm/174040047025?var=472854321933) |

---

## Network

The Hi-Fi system runs on a dedicated isolated VLAN with no internet access initiated from within the zone. The Roon core communicates with endpoints across VLANs via selective mDNS forwarding on the MikroTik router. Roon ARC is configured for remote access over both IPv4 and IPv6.

Read more about the network setup in [this post](/posts/home-network-rebuild/).

---

## Software

- **Roon** — music management, DSP, and endpoint control
- **Roon ARC** — remote playback anywhere in the world