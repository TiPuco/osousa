---
title: "About"
layout: "single"
url: "/about/"
summary: "About Osvaldo Sousa"
---

<img src="/img/about.jpg" alt="Osvaldo Sousa" style="width:100%; border-radius:12px; max-height:400px; object-fit:cover; object-position:center top; margin-bottom:1.5rem;">

## Hi, I'm Osvaldo

I'm a Mozambican IT professional with over 20 years of experience, currently working as a **Cybersecurity Analyst** at Hidroeléctrica de Cahora Bassa (HCB) — one of Africa's largest hydroelectric power plants. My career has taken me through systems analysis, networking, service desk management, and now security operations in critical infrastructure.

I'm based between **Songo, Tete** and **Maputo**, Mozambique, and I write here about infosec, networking, homelabs, and whatever I happen to be learning or breaking at any given moment.

---

<div style="display:flex; gap:1rem; margin-bottom:2rem; border-bottom:1px solid var(--border);">
  <button onclick="showTab('personal')" id="tab-personal"
    style="padding:0.6rem 1.5rem; background:none; border:none; border-bottom:3px solid var(--primary); color:var(--primary); font-size:1rem; font-weight:600; cursor:pointer;">
    Personal
  </button>
  <button onclick="showTab('professional')" id="tab-professional"
    style="padding:0.6rem 1.5rem; background:none; border:none; border-bottom:3px solid transparent; color:var(--secondary); font-size:1rem; cursor:pointer;">
    Professional
  </button>
</div>

<div id="tab-content-personal">

### Who I Am Outside Work

**Photography**
I shoot with an Olympus OM-D E-M10 Mark II and a 12-40mm f/2.8 Pro lens. I'm drawn to portraits and available light situations. Photography and security share more than people think — both reward patience and attention to detail.

**Hi-Fi Audio & Acoustics**
I run a dedicated audio setup with a Roon music server and a high-end network streamer on its own isolated VLAN. If you want to know why, read [this post](/posts/home-network-rebuild/).

**Home Lab**
My home network is a project that never ends. MikroTik, UniFi, Raspberry Pi, Docker. Currently planning a Proxmox node for security research and testing.

**Football**
Manchester United supporter. Results not always matching expectations, but loyalty is unconditional.

### Languages

- **Portuguese** — Native
- **English** — Fluent

</div>

<div id="tab-content-professional" style="display:none;">

### Career Timeline

**2024 — Present · Cyber Security Analyst**
Hidroeléctrica de Cahora Bassa · Songo, Tete
Security operations, incident handling, threat monitoring and response in a critical infrastructure environment.

**2014 — 2024 · Systems Analyst**
Hidroeléctrica de Cahora Bassa · Songo, Tete
Over a decade supporting the operational and business technology needs of HCB across systems, infrastructure, and integrations.

**2012 — 2013 · Analyst Programmer**
Hidroeléctrica de Cahora Bassa · Songo, Tete

**2006 — 2012 · IT Area Responsible MZ & SA**
Grupo Pestana · Mozambique & South Africa
Managed IT operations across Mozambique and South Africa for one of Portugal's largest hospitality groups.

**2011 — 2012 · Administrator**
Netop Lda. · Maputo

**2005 — 2006 · Director**
IT&Dreams, Lda

---

### Certifications

| Certification | Issuer |
|---|---|
| GIAC Security Essentials (GSEC) | GIAC / SANS |
| GIAC Security Operations Certified (GSOC) | GIAC / SANS |
| Cisco CCNA | ISCTEM Cisco CCNA Academy |
| D-Link Certified Engineer | D-Link Academy South Africa |

### Training

| Course | Code |
|---|---|
| Hacker Tools, Techniques & Incident Handling (GCIH) | SEC504 |
| Security Essentials: Network, Endpoint and Cloud | SEC401 |
| SOC Analyst Training — Applied Skills for Cyber Defense | SEC450 |
| Red Hat System Administration I — RHEL 8 | RH124 |
| Red Hat System Administration II — RHEL 8 | RH134 |
| Red Hat System Administration III: Linux Automation | — |
| HP Data Protector | — |
| HPE 3Par Storage Administration | — |
| HPE Blade System Administration | — |
| VMware vSphere | — |
| Microsoft Windows Server 2012 R2 | — |
| ITIL | — |

### Technical Skills

**Security**
Cybersecurity · SOC · Incident Response · Malware Analysis · Web Application Security · Vulnerability Management · Network Security · Linux Security · Windows Security · Cyber Defense · Access Control · Security Policy

**Networking**
TCP/IP · CCNA · Cisco Technologies · Routing · OSPF · Switches · LAN · VPN · DNS · Network Administration

**Systems & Infrastructure**
Linux · RHEL · Windows Server · Active Directory · VMware · Virtualization · Mac OS · HPE Systems · System Administration

**Development & Databases**
Web Development · PHP · Microsoft SQL Server

**Management**
IT Management · Service Desk Management · ITIL · Troubleshooting · IT Operations

### Recognition

🏆 **Ambassador of Innovation** — Hidroeléctrica de Cahora Bassa

### Languages

- **Portuguese** — Native
- **English** — Fluent

</div>

---

Feel free to connect with me on [LinkedIn](https://www.linkedin.com/in/osvaldodesousa/) — or if you prefer, use the [contact form](/contact/) to send me a message directly.

<script>
function showTab(tab) {
  document.getElementById('tab-content-professional').style.display = tab === 'professional' ? 'block' : 'none';
  document.getElementById('tab-content-personal').style.display = tab === 'personal' ? 'block' : 'none';
  document.getElementById('tab-professional').style.borderBottom = tab === 'professional' ? '3px solid var(--primary)' : '3px solid transparent';
  document.getElementById('tab-professional').style.color = tab === 'professional' ? 'var(--primary)' : 'var(--secondary)';
  document.getElementById('tab-professional').style.fontWeight = tab === 'professional' ? '600' : 'normal';
  document.getElementById('tab-personal').style.borderBottom = tab === 'personal' ? '3px solid var(--primary)' : '3px solid transparent';
  document.getElementById('tab-personal').style.color = tab === 'personal' ? 'var(--primary)' : 'var(--secondary)';
  document.getElementById('tab-personal').style.fontWeight = tab === 'personal' ? '600' : 'normal';
}
</script>