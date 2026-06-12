# HuntPack

> A growing collection of CrowdStrike CQL threat-hunting packs — each one a self-contained HTML report with the hunt hypothesis, MITRE mapping, copy-paste CQL queries, triage checklist, and hardening guidance.

Reports live in [`hunts/`](hunts/) as standalone HTML files. **Browse the whole library at [slapopotamus.github.io/HuntPack](https://slapopotamus.github.io/HuntPack)** — or use the **Preview** link on any hunt below to open its rendered report (the **Source** link shows the raw file on GitHub).

---

## Hunts

<!-- HUNTS_TABLE:START -->

| Hunt | Type | Severity |
| --- | --- | --- |
| [ConsentFix — Entra ID OAuth Phishing & Token Theft](https://slapopotamus.github.io/HuntPack/hunts/ConsentFix-Hunt.html) | Identity / OAuth token theft → ATO | ACTIVE · MFA BYPASS |
| [RoguePlanet — Microsoft Defender SYSTEM Escalation Zero-Day](https://slapopotamus.github.io/HuntPack/hunts/RoguePlanet-Hunt.html) | LPE / AV-abuse zero-day (RCE variant via SMB) | PoC PUBLIC · NO PATCH |
| [WinRAR CVE-2025-8088 — Russia-Aligned Stealer Campaigns](https://slapopotamus.github.io/HuntPack/hunts/WinRAR-CVE-2025-8088-Hunt.html) | Espionage + infostealer via spearphishing | NATION-STATE · ITW |
| [The Gentlemen — Ransomware Hunt & Hardening Pack](https://slapopotamus.github.io/HuntPack/hunts/TheGentlemen-RansomwareHunt.html) | Ransomware · double extortion · self-propagating | ACTIVE RaaS |
| [CVE-2026-41091 — Microsoft Defender Link-Following Elevation of Privilege](https://slapopotamus.github.io/HuntPack/hunts/CVE-2026-41091-Hunt.html) | LPE → SYSTEM · EDR tampering | CVSS 7.8 |
| [INC Ransom — Rapid Extortion Against Professional-Services Firms](https://slapopotamus.github.io/HuntPack/hunts/INC-Ransom-Hunt.html) | Ransomware · Double extortion | HIGH URGENCY |
| [Salt Typhoon / UAT-9244 — TernDoor · PeerTime · BruteEntry](https://slapopotamus.github.io/HuntPack/hunts/Salt-Typhoon-UAT-9244-Hunt.html) | Nation-state espionage · telecom | HIGH |
| [CVE-2026-41089 — Windows Netlogon RCE (Domain Controller Takeover)](https://slapopotamus.github.io/HuntPack/hunts/CVE-2026-41089-Netlogon-Hunt.html) | Pre-auth RCE · Identity / AD | CVSS 9.8 |
| [ShaiHulud — Hades Wave: PyPI Bioinformatics & Science Package Trojanization](https://slapopotamus.github.io/HuntPack/hunts/ShaiHulud-Hades-PyPI-Hunt.html) | Supply Chain Worm · Credential Stealer |  |
| [IronWorm — npm Supply-Chain Worm HuntPack](https://slapopotamus.github.io/HuntPack/hunts/IronWorm-Hunt.html) |  |  |
| [UNC3753 — "Silent Ransom Group" Vishing & Data-Theft Extortion HuntPack](https://slapopotamus.github.io/HuntPack/hunts/UNC3753-Hunt.html) |  |  |
| [MuddyWater](https://slapopotamus.github.io/HuntPack/hunts/MuddyWater-Hunt.html) |  |  |
| [SocGholish](https://slapopotamus.github.io/HuntPack/hunts/SocGholish-Hunt.html) |  |  |
| [Qilin Ransomware - Defender Hunt & Hardening Pack](https://slapopotamus.github.io/HuntPack/hunts/Qilin-Hunt.html) |  |  |
| [LummaC2 Hunt](https://slapopotamus.github.io/HuntPack/hunts/LummaC2-Hunt.html) |  |  |
| [Mini Shai-Hulud — Defender Hunt & Hardening Pack](https://slapopotamus.github.io/HuntPack/hunts/Mini-Shai-Hulud-Hunt.html) |  |  |
| [Amber Albatross — Hunt & Hardening Pack](https://slapopotamus.github.io/HuntPack/hunts/AmberAlbatross-Hunt.html) |  |  |
| [Drift Token — SaaS Supply-Chain OAuth Theft Hunt & Hardening Pack](https://slapopotamus.github.io/HuntPack/hunts/DriftToken-SalesforceOAuthHunt.html) |  |  |
| [APT28 PRISMEX / Operation Neusploit — Hunt & Hardening Pack](https://slapopotamus.github.io/HuntPack/hunts/APT28-PRISMEX-Hunt.html) |  |  |
| [Medusa BYOVD — Hunt Package](https://slapopotamus.github.io/HuntPack/hunts/Medusa-BYOVD-Hunt.html) |  |  |
| [MIMICRAT / ClickFix — Hunt Package](https://slapopotamus.github.io/HuntPack/hunts/MimiCRAT-Hunt.html) |  |  |
| [NetSupport Manager - Defender Hunt & Hardening Pack](https://slapopotamus.github.io/HuntPack/hunts/NetSupportManager-Hunt.html) |  |  |
| [Scarlet Goldfinch](https://slapopotamus.github.io/HuntPack/hunts/ScarletGoldfinch-Hunt.html) |  |  |
| [Phantom in the Vault — Hunt Package](https://slapopotamus.github.io/HuntPack/hunts/PhantomVault-Hunt.html) |  |  |
| [PayoutsKing](https://slapopotamus.github.io/HuntPack/hunts/PayoutsKing-Hunt.html) |  |  |
| [QEMU Hidden-VM Abuse — Hunt Package](https://slapopotamus.github.io/HuntPack/hunts/QEMU-Hunt.html) |  |  |
| [Operation SilentCanvas — Hunt Package](https://slapopotamus.github.io/HuntPack/hunts/SilentCanvas-Hunt.html) |  |  |
| [Tampered Chef - Defender Hunt & Hardening Pack](https://slapopotamus.github.io/HuntPack/hunts/TamperedChef-Hunt.html) |  |  |

<!-- HUNTS_TABLE:END -->

### ConsentFix — Entra ID OAuth Phishing & Token Theft
**Lure → legit first-party-app sign-in → victim pastes the localhost auth-code URL → attacker redeems it for access + refresh tokens and operates from their own infra. MFA & most Conditional Access bypassed. Identity-log hunt — detection lives in Entra, not the endpoint.**
**Threat:** ConsentFix (OAuth consent/auth-code phishing) · **Type:** Identity / OAuth token theft → ATO · **Severity:** ACTIVE · MFA BYPASS

[Preview](https://slapopotamus.github.io/HuntPack/hunts/ConsentFix-Hunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/ConsentFix-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/ConsentFix-Hunt.html)

---

### RoguePlanet — Microsoft Defender SYSTEM Escalation Zero-Day
**TOCTOU race in Defender's file-processing path → NTFS junction redirect → MsMpEng.exe (SYSTEM) writes/executes attacker content on fully-patched Windows 10/11. Defensive hunt & harden pack — no exploit code.**
**Threat:** RoguePlanet · Nightmare Eclipse · **Type:** LPE / AV-abuse zero-day (RCE variant via SMB) · **Severity:** PoC PUBLIC · NO PATCH

[Preview](https://slapopotamus.github.io/HuntPack/hunts/RoguePlanet-Hunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/RoguePlanet-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/RoguePlanet-Hunt.html)

---

### WinRAR CVE-2025-8088 — Russia-Aligned Stealer Campaigns
**Path-traversal via NTFS ADS (patched WinRAR 7.13, Jul 2025, still exploited) → Startup-folder LNK → cmd → PowerShell → GIFTEDCROOK , plus Gamaredon's HTA→VBScript GammaLoad/GammaSteel. Defensive hunt & harden pack — no exploit code.**
**Threat:** UAC-0226 / SHADOW-EARTH-066 · Earth Dahu / Gamaredon · **Type:** Espionage + infostealer via spearphishing · **Severity:** NATION-STATE · ITW

[Preview](https://slapopotamus.github.io/HuntPack/hunts/WinRAR-CVE-2025-8088-Hunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/WinRAR-CVE-2025-8088-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/WinRAR-CVE-2025-8088-Hunt.html)

---

### The Gentlemen — Ransomware Hunt & Hardening Pack
**FortiOS exploit (CVE-2024-55591) → AD recon → BYOVD EDR-kill → self-propagating Go encryptor ( .i8p14s ). Defensive hunt & harden pack — no exploit code.**
**Threat:** The Gentlemen · Storm-2697 · Phantom Mantis · **Type:** Ransomware · double extortion · self-propagating · **Severity:** ACTIVE RaaS

[Preview](https://slapopotamus.github.io/HuntPack/hunts/TheGentlemen-RansomwareHunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/TheGentlemen-RansomwareHunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/TheGentlemen-RansomwareHunt.html)

---

### CVE-2026-41091 — Microsoft Defender Link-Following Elevation of Privilege
**Actively exploited June 2026 Patch Tuesday zero-day. The Malware Protection Engine follows symlinks/junctions before a privileged file op, letting a local attacker reach SYSTEM. Seen in the wild in the "Nightmare Eclipse" Defender exploit wave (BlueHammer / RedSun / UnDefend), chained from compromised FortiGate SSL VPN access. Defensive hunt & harden pack — no exploit code.**
**Type:** LPE → SYSTEM · EDR tampering · **Severity:** CVSS 7.8

[Preview](https://slapopotamus.github.io/HuntPack/hunts/CVE-2026-41091-Hunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/CVE-2026-41091-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/CVE-2026-41091-Hunt.html)

---

### INC Ransom — Rapid Extortion Against Professional-Services Firms
**RaaS double-extortion operation clustering attacks on legal & professional-services firms in 2026. Defensive hunt & harden pack — no exploit code.**
**Threat:** INC Ransom (G1032) · **Aliases:** GOLD IONIC · Tarnished Scorpion · **Type:** Ransomware · Double extortion · **Initial access:** Edge / VPN / RMM (3 KEV CVEs) · **Severity:** HIGH URGENCY

[Preview](https://slapopotamus.github.io/HuntPack/hunts/INC-Ransom-Hunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/INC-Ransom-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/INC-Ransom-Hunt.html)

---

### Salt Typhoon / UAT-9244 — TernDoor · PeerTime · BruteEntry
**China-nexus telecom espionage toolkit. Windows backdoor (TernDoor), cross-arch ELF P2P backdoor (PeerTime), and a GoLang edge-device brute-force ORB (BruteEntry). Defensive hunt & harden pack — no offensive tradecraft.**
**Type:** Nation-state espionage · telecom · **Severity:** HIGH

[Preview](https://slapopotamus.github.io/HuntPack/hunts/Salt-Typhoon-UAT-9244-Hunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/Salt-Typhoon-UAT-9244-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/Salt-Typhoon-UAT-9244-Hunt.html)

---

### CVE-2026-41089 — Windows Netlogon RCE (Domain Controller Takeover)
**Unauthenticated 0-click stack overflow in netlogon.dll → SYSTEM on any Domain Controller. Defensive hunt & harden pack — no exploit code.**
**Type:** Pre-auth RCE · Identity / AD · **Severity:** CVSS 9.8

[Preview](https://slapopotamus.github.io/HuntPack/hunts/CVE-2026-41089-Netlogon-Hunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/CVE-2026-41089-Netlogon-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/CVE-2026-41089-Netlogon-Hunt.html)

---

### ShaiHulud — Hades Wave: PyPI Bioinformatics & Science Package Trojanization
**Supply chain worm targeting 19 scientific PyPI packages — credential theft, CI/CD pivot, & SLSA provenance forgery**
**Threat:** Shai-Hulud / Hades (TeamPCP) · **Type:** Supply Chain Worm · Credential Stealer

[Preview](https://slapopotamus.github.io/HuntPack/hunts/ShaiHulud-Hades-PyPI-Hunt.html) · [IOC Quick-Copy ↗](https://slapopotamus.github.io/HuntPack/hunts/ShaiHulud-Hades-PyPI-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/ShaiHulud-Hades-PyPI-Hunt.html)

---

### IronWorm — npm Supply-Chain Worm HuntPack

[Preview](https://slapopotamus.github.io/HuntPack/hunts/IronWorm-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/IronWorm-Hunt.html)

---

### UNC3753 — "Silent Ransom Group" Vishing & Data-Theft Extortion HuntPack

[Preview](https://slapopotamus.github.io/HuntPack/hunts/UNC3753-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/UNC3753-Hunt.html)

---

### MuddyWater

[Preview](https://slapopotamus.github.io/HuntPack/hunts/MuddyWater-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/MuddyWater-Hunt.html)

---

### SocGholish

[Preview](https://slapopotamus.github.io/HuntPack/hunts/SocGholish-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/SocGholish-Hunt.html)

---

### Qilin Ransomware - Defender Hunt & Hardening Pack
**Hunt package for Qilin ransomware activity with Red Canary's 2026 ransomware trend page as the primary source. It separates Red Canary-observed facts from enrichment and adjacent campaign pivots, then turns them into Falcon LogScale CQL, Falcon Custom IOA candidates, IOC action guidance, validation gates, hardening, and containment playbooks.**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/Qilin-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/Qilin-Hunt.html)

---

### LummaC2 Hunt

[Preview](https://slapopotamus.github.io/HuntPack/hunts/LummaC2-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/LummaC2-Hunt.html)

---

### Mini Shai-Hulud — Defender Hunt & Hardening Pack
**Refreshed hunt package for the May 2026 Mini Shai-Hulud npm/PyPI worm (TeamPCP, CVE-2026-45321). v5.1 refreshes the hunt pack with native audit-log hunts, machine-readable IOC appendices, validation gates, telemetry gaps, the May 19 Socket-reported @antv wave, the t.m-kosche.com exfil endpoint, updated IOC and package pivots, and reviewed Falcon LogScale CQL plus Custom IOA guidance for confirmed artifacts, C2/payload infrastructure, package-manager lifecycle execution, developer-secret access, GitHub Actions workflow tampering, dead-drop repository creation, CI runner exposure, and IMDS credential-harvest behavior.**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/Mini-Shai-Hulud-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/Mini-Shai-Hulud-Hunt.html)

---

### Amber Albatross — Hunt & Hardening Pack
**Red Canary–tracked Windows activity cluster. PUP installer / fake-PDF-utility lure → InnoSetup → Base64-encoded PowerShell → Pyarmor-obfuscated PyInstaller stealer requiring --safetorun --channel=<hex> to run. 11 abused EV code-signing certificates. Switchable Falcon cloud for shareable deep-links.**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/AmberAlbatross-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/AmberAlbatross-Hunt.html)

---

### Drift Token — SaaS Supply-Chain OAuth Theft Hunt & Hardening Pack
**UNC6395 / Salesloft Drift / Salesforce data-theft campaign (Aug 8–18, 2025) & the secondary breach wave it kicked off (AWS keys, Snowflake tokens, Slack tokens harvested from support cases). Switchable Falcon cloud for shareable deep-links.**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/DriftToken-SalesforceOAuthHunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/DriftToken-SalesforceOAuthHunt.html)

---

### APT28 PRISMEX / Operation Neusploit — Hunt & Hardening Pack
**CVE-2026-21509 (Office RTF RCE) → PrismexLoader / PixyNetLoader → CovenantGrunt over filen.io. NotDoor Outlook backdoor for long-haul persistence. Switchable Falcon cloud for shareable deep-links.**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/APT28-PRISMEX-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/APT28-PRISMEX-Hunt.html)

---

### Medusa BYOVD — Hunt Package
**Medusa ransomware (operator: Spearwing) using ABYSSWORKER · POORTRY · KillAV driver family to terminate EDR/AV processes prior to gaze.exe encryption**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/Medusa-BYOVD-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/Medusa-BYOVD-Hunt.html)

---

### MIMICRAT / ClickFix — Hunt Package
**ClickFix clipboard PowerShell → ETW/AMSI bypass → Lua 5.4.7 loader → Meterpreter shellcode → MIMICRAT native-C++ beacon (mimics multiple C2 frameworks) · Generated 2026-05-12 · Source: Elastic Security Labs**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/MimiCRAT-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/MimiCRAT-Hunt.html)

---

### NetSupport Manager - Defender Hunt & Hardening Pack
**Hunt package for Red Canary's NetSupport Manager threat page and related Scarlet Goldfinch, SocGholish, ClickFix, phishing, and RMM-abuse reporting. Focuses on suspicious NetSupport Client deployments, renamed client32 binaries, non-standard installation paths, attacker-controlled configuration files, persistence, remote-control traffic, and delivery chains using JavaScript, PowerShell, curl, msiexec, mshta, finger, forfiles, WMI, archives, and scheduled tasks.**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/NetSupportManager-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/NetSupportManager-Hunt.html)

---

### Scarlet Goldfinch

[Preview](https://slapopotamus.github.io/HuntPack/hunts/ScarletGoldfinch-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/ScarletGoldfinch-Hunt.html)

---

### Phantom in the Vault — Hunt Package
**REF6598 · Obsidian Shell-Commands plugin abuse → PhantomPull loader → PhantomPulse RAT (Windows + macOS) · Blockchain-based C2 dead-drop · Generated 2026-05-12 · Source: Elastic Security Labs**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/PhantomVault-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/PhantomVault-Hunt.html)

---

### PayoutsKing

[Preview](https://slapopotamus.github.io/HuntPack/hunts/PayoutsKing-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/PayoutsKing-Hunt.html)

---

### QEMU Hidden-VM Abuse — Hunt Package
**Payouts King / STAC4713 & STAC3725 · qemu-system-x86_64.exe used as stealth backdoor · Generated 2026-05-13 · Source: Sophos**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/QEMU-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/QEMU-Hunt.html)

---

### Operation SilentCanvas — Hunt Package
**JPEG-extension PowerShell loader → trojanized ConnectWise ScreenConnect · Generated 2026-05-12 · Source: Cyfirma**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/SilentCanvas-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/SilentCanvas-Hunt.html)

---

### Tampered Chef - Defender Hunt & Hardening Pack
**CrowdStrike Falcon LogScale hunt package for Red Canary's Tampered Chef tracking: signed fake productivity applications such as RecipeLister and Calendaromatic that hide JavaScript command content inside legitimate-looking API responses, manipulate Chrome/search behavior, and overlap with broader TamperedChef-style malvertising clusters distributing PDF tools, NeutralinoJS/Electron apps, RATs, stealers, and browser hijackers.**

[Preview](https://slapopotamus.github.io/HuntPack/hunts/TamperedChef-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/hunts/TamperedChef-Hunt.html)

---

## How to use

1. Open the **Preview** link for the hunt you're interested in — it renders the full HTML report directly from this repo.
2. Copy the CQL queries into Falcon LogScale / NG-SIEM and tune the time window for your environment.
3. Walk the triage checklist on any hit.
4. Apply the hardening guidance to close the gap.

## What's inside each pack

Every HuntPack report follows the same structure:

- **Hypothesis** — what the adversary does and why this hunt catches it
- **MITRE ATT&CK mapping** — techniques, tactics, and sub-techniques
- **CQL queries** — ready-to-run detections with field references
- **Triage checklist** — what to pivot on when a query lights up
- **Hardening** — GPO, registry, ASR, and configuration changes to prevent the TTP

## Platform

Built for **CrowdStrike Falcon LogScale** and **Falcon Next-Gen SIEM** (CQL). Queries reference standard Falcon telemetry — `#event_simpleName`, `ProcessRollup2`, `DnsRequest`, `NetworkConnectIP4`, AD events, identity events, etc.

## Templates

Reusable authoring assets live in [templates](templates/): the HuntPack HTML template, authoring guide, and intake JSON. New packs should include a source-review / web-hunter pass before query writing so IOCs, IOAs, and references are corroborated instead of single-sourced.

## Contributing

Hunts live as single-file HTML reports so they're easy to share, version, and preview without a build step. PRs welcome.

## License

This project is licensed under the [MIT License](LICENSE).
