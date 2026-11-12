---
title: "Projects"
layout: "single"
url: "/projects/"
summary: "Tools, builds and experiments by Osvaldo de Sousa"
description: "Open-source tools, homelab builds and other hands-on projects by Osvaldo de Sousa."
ShowReadingTime: false
ShowBreadCrumbs: false
hidemeta: true
comments: false
---

Things I've built, broken, fixed and shared. Each project links to its code or to the posts that tell the story behind it.

<style>
.proj-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:1rem;margin-top:1.5rem}
.proj-card{background:var(--entry);border:1px solid var(--border);border-radius:8px;padding:1.2rem 1.3rem;display:flex;flex-direction:column}
.post-content .proj-card h3{margin:0 0 .5rem;font-size:1.15rem}
.post-content .proj-card p{margin:0 0 .9rem;color:var(--secondary);font-size:.95rem;flex:1}
.proj-status{font-size:.7rem;text-transform:uppercase;letter-spacing:.08rem;color:var(--accent);font-weight:600;margin-bottom:.3rem}
.proj-tags{display:flex;flex-wrap:wrap;gap:.4rem;margin-bottom:1rem}
.proj-tags span{font-size:.75rem;padding:.15rem .55rem;border-radius:999px;border:1px solid var(--border);color:var(--secondary)}
.post-content .proj-links a{color:var(--accent);font-weight:600;font-size:.9rem;margin-right:1rem;box-shadow:none;text-decoration:none}
.post-content .proj-links a:hover{text-decoration:underline}
</style>

<div class="proj-grid">
<div class="proj-card">
<div class="proj-status">Released</div>
<h3>Taskbar Auto-Align</h3>
<p>PowerShell tool that centers the Windows 11 taskbar when an external monitor is connected and left-aligns it on the laptop screen alone. Event-driven, works with any monitor brand, on x64 and ARM64.</p>
<div class="proj-tags"><span>PowerShell</span><span>Windows 11</span><span>Task Scheduler</span></div>
<div class="proj-links"><a href="https://github.com/TiPuco/taskbar-auto-align" target="_blank" rel="noopener">GitHub →</a><a href="/posts/windows-taskbar-auto-align/">Read the post →</a></div>
</div>
<div class="proj-card">
<div class="proj-status">Ongoing</div>
<h3>Dzua Homelab</h3>
<p>A Proxmox homelab built around a Minisforum MS-01: VLAN-segmented network, Wazuh SIEM, Grafana monitoring, privileged access through JumpServer, and automated UPS shutdown.</p>
<div class="proj-tags"><span>Proxmox</span><span>MikroTik</span><span>Wazuh</span><span>Grafana</span></div>
<div class="proj-links"><a href="/posts/minisforum-ms01-plan-and-purchase/">The plan →</a><a href="/posts/dzua-homelab-journey/">The journey →</a></div>
</div>
<div class="proj-card">
<div class="proj-status">Live</div>
<h3>osousa.com</h3>
<p>This site. Hugo with the PaperMod theme and customised layouts, deployed automatically to Cloudflare Pages on every Git push. The CV is typeset in LaTeX, with a QR code back to its latest version.</p>
<div class="proj-tags"><span>Hugo</span><span>Cloudflare Pages</span><span>LaTeX</span></div>
<div class="proj-links"><a href="/cv/">View the CV →</a></div>
</div>
</div>
