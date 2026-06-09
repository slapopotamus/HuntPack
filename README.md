# HuntPack

> A growing collection of CrowdStrike CQL threat-hunting packs — each one a self-contained HTML report with the hunt hypothesis, MITRE mapping, copy-paste CQL queries, triage checklist, and hardening guidance.

Every file in this repo is a standalone HTML report. Use the **Preview** link to render it in your browser via [htmlpreview.github.io](https://htmlpreview.github.io), or the **Source** link to view the raw file on GitHub.

---

## Hunts

### CVE-2026-41089 — Windows Netlogon RCE (Domain Controller Takeover)
**Pre-auth 0-click stack overflow in `netlogon.dll` → SYSTEM on any Domain Controller**
HuntPack v0.2 for CVE-2026-41089 (CVSS 9.8, CWE-121) — a stack-based buffer overflow in the Windows Netlogon RPC service (`netlogon.dll`, `BuildSamLogonResponse`). Because every Domain Controller runs Netlogon, any reachable DC is structurally exposed; exploitation is 0-click, unauthenticated, and low-complexity. Patched 2026-05-12 (Patch Tuesday), in-the-wild ~2026-05-29. Covers 8 Falcon LogScale CQL hunts, 5 native audit-log hunts, 4 Custom IOA candidates, consolidated + machine-readable IOC appendices with a grouped IOC quick-copy grid, detection validation gates, tiered DC hardening, 3 deployable playbooks, and a containment runbook. Built from MSRC + CVE.org + NVD + CCB Belgium intel.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/CVE-2026-41089-Netlogon-Hunt.html) · [IOC Quick-Copy ↗](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/CVE-2026-41089-Netlogon-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/CVE-2026-41089-Netlogon-Hunt.html)

---

### Shai-Hulud "Descends to Hades" — PyPI Wave Hunt & Hardening Pack
**Cross-ecosystem supply-chain worm / malicious PyPI packages / Python `.pth` → Bun payload**
HuntPack v0.2 for the Shai-Hulud "Hades" PyPI wave — covers the Python `.pth` startup hook that bootstraps a Bun runtime from a pinned GitHub release, the `.bun_ran` execution sentinel, CI/CD and EDR sandbox-evasion checks, credential-file sweeps (`.aws/credentials`, `.npmrc`, SSH keys), C2 exfil domains, GitHub dead-drop markers, 13 Falcon LogScale CQL hunts with one-click "Open in Falcon" deep-links, Custom IOA candidates, detection validation gates, a grouped IOC quick-copy panel (hashes, network, file paths, 25 malicious PyPI packages / 43 version pins, hunt strings, crypto keys), and deployable hardening playbooks.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/ShaiHulud-Hades-PyPI-Hunt.html) · [IOC Quick-Copy ↗](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/ShaiHulud-Hades-PyPI-Hunt.html#s10) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/ShaiHulud-Hades-PyPI-Hunt.html)

---

### IronWorm — npm Supply-Chain Worm Hunt
**Rust credential-stealer & self-replicating npm worm / preinstall ELF / eBPF rootkit**
Behavior-first HuntPack for IronWorm — a custom Rust implant distributed through 37 trojanized npm package versions published from a single compromised maintainer account. It executes via a malicious `preinstall` script (`tools/setup`, with a `.github/scripts/precheck` variant) the moment `npm install` runs — a UPX-stubbed, string-encrypted ELF that fires before dependency resolution. Once running it sweeps 86 environment variables and 20+ credential file paths (AWS/GCP/Azure, npm, GitHub, SSH, Docker, Vault, Kubernetes, and the 2026 AI-provider keys — Anthropic, OpenAI, Gemini, Cohere, Mistral, Groq, Perplexity, xAI), injects a JavaScript hook into the Exodus desktop wallet to steal the password and seed phrase, loads an eBPF kernel rootkit to hide processes/sockets and resist `ptrace`, bootstraps Tor and beacons to `/api/agent` for tasking, and self-replicates — abusing npm Trusted Publishing (OIDC token exchange) in CI to re-publish trojanized packages. Covers Falcon LogScale CQL hunts, native npm/GitHub/CI audit-log checks, Custom IOA guidance, machine-readable IOC appendices, validation gates, and hardening.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/IronWorm-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/IronWorm-Hunt.html)

---

### UNC3753 — "Silent Ransom Group" Hunt
**Vishing / data-theft extortion (Luna Moth / Chatty Spider) — RMM abuse & rapid exfil**
Behavior-first HuntPack for UNC3753 (aka Luna Moth, Chatty Spider, Silent Ransom Group) — a financially motivated cluster that phones employees posing as internal IT, talks them onto a screen-share, plants a commercial RMM agent, then enumerates document stores and exfiltrates sensitive files, often within a single business day (with in-person USB theft as a fallback). Hunt focus: unauthorized RMM / remote-support tooling, curl→msiexec install chains, Rclone/WinSCP egress, outbound SSH, USB mass-storage, and known C2 IPs — with Falcon LogScale CQL hunts, triage checklist, and hardening.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/UNC3753-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/UNC3753-Hunt.html)

---

### MuddyWater — Defender Hunt & Hardening Pack
**Iranian MOIS nation-state APT / PowerShell + RMM abuse / espionage & persistence**
Behavior-first HuntPack for MuddyWater (Iran MOIS, active since 2017) targeting government, telecom, oil & gas, defense, and finance across the Middle East, Asia, Europe, and North America. Covers heavy PowerShell at every kill-chain stage, systematic RMM-tool abuse (Atera, SimpleHelp, ScreenConnect, N-able, Action1, PDQ, Level) delivered from free file-sharing services, compromised-mailbox spearphishing, GoogleUpdate.exe DLL sideloading, and recent backdoors (BugSleep, Phoenix v4, UDPGangster, MuddyViper via the "Fooder" reflective loader, VAX One) — with Falcon LogScale CQL hunts, Custom IOA guidance, validation gates, and hardening.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/MuddyWater-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/MuddyWater-Hunt.html)

---

### SocGholish — Defender Hunt & Hardening Pack
**JavaScript loader / fake browser-update drive-by (Mustard Tempest / GOLD PRELUDE → Evil Corp)**
Behavior-first HuntPack for SocGholish (FakeUpdates) — a JavaScript-based loader delivered via compromised websites posing as browser updates. Operated by Mustard Tempest (GOLD PRELUDE), with access sold to Indrik Spider (Evil Corp) for ransomware deployment; ranked #8 in the 2026 Red Canary Threat Detection Report. Covers drive-by compromise and fake-update lures, JavaScript/WScript execution, recon and second-stage delivery, AD-targeted follow-on, RansomHub-via-MintsLoader handoff, Falcon LogScale CQL hunts, Custom IOA guidance, validation gates, and hardening.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/SocGholish-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/SocGholish-Hunt.html)

---

### Qilin Ransomware Hunt
**Ransomware-as-a-Service / Veeam exploitation / RMM and ESXi impact**
Hunt pack for Red Canary's Qilin ransomware coverage and related Cybernews, Sophos, Trend Micro, Microsoft, HHS, CIS/MS-ISAC, Halcyon, and CrowdStrike enrichment - covers Veeam CVE-2023-27532/CVE-2024-40711 precursors, Admon admin creation, GPO-based Chrome credential theft, ScreenConnect/MSP pivoting, recovery inhibition, ESXi/Linux behavior, IOC action guidance, Falcon LogScale CQL hunts, Custom IOA candidates, validation gates, hardening, and containment.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/Qilin-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/Qilin-Hunt.html)

---

### LummaC2 Hunt
**Windows infostealer / fake CAPTCHA delivery / browser credential theft**
Defender hunt package for Red Canary's LummaC2 tracking and related Microsoft, FBI/CISA, CIS, MITRE, and Bitdefender enrichment - covers mshta-to-PowerShell delivery, fodhelper and OpenWith UAC bypass pivots, Chrome remote-debugging abuse, browser credential theft, staging artifacts, C2 infrastructure, Falcon LogScale CQL hunts, Custom IOA guidance, IOC action handling, validation gates, hardening, and containment.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/LummaC2-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/LummaC2-Hunt.html)

---

### Mini Shai-Hulud — Defender Hunt & Hardening Pack
**Active npm/PyPI supply-chain worm (TeamPCP / CVE-2026-45321)**
Refreshed defender hunt package for the May 2026 Mini Shai-Hulud campaign — covers CrowdStrike LogScale CQL hunts, native GitHub/npm/PyPI/cloud audit-log checks, confirmed artifacts, C2/payload infrastructure, package-manager lifecycle execution, developer-secret access, GitHub Actions workflow tampering, dead-drop repository creation, CI runner exposure, IMDS credential-harvest behavior, Custom IOA guidance, machine-readable IOC appendices, detection validation gates, and deployable hardening playbooks.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/Mini-Shai-Hulud-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/Mini-Shai-Hulud-Hunt.html)

---

### Amber Albatross Hunt
**Pyarmor-obfuscated PyInstaller stealer (Red Canary 2026 TDR #1)**
PUP-and-fake-PDF-utility delivery → Base64-encoded PowerShell → Pyarmor PyInstaller binary that runs only with `--safetorun --channel=<hex>`. Covers the 11 abused EV code-signing thumbprints, 12 published C2 domains, Chrome `CloudManagementEnrollmentToken` recon, browser-profile theft, and a honey-token canary recipe.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/AmberAlbatross-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/AmberAlbatross-Hunt.html)

---

### Drift Token — Salesforce OAuth Hunt
**SaaS supply-chain OAuth theft (UNC6395 / Salesloft Drift)**
Hunt for abuse of stolen Drift OAuth tokens against Salesforce orgs — covers token replay, suspicious Bulk API exports, and downstream credential pivots.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/DriftToken-SalesforceOAuthHunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/DriftToken-SalesforceOAuthHunt.html)

---

### APT28 — PRISMEX Hunt
**Russian GRU webmail / cloud mailbox compromise activity**
Detections for APT28 / Fancy Bear PRISMEX-aligned tradecraft — credential harvesting, OAuth abuse, and lateral movement against M365 and Exchange.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/APT28-PRISMEX-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/APT28-PRISMEX-Hunt.html)


---

### Medusa — BYOVD Hunt
**Medusa ransomware bring-your-own-vulnerable-driver activity**
Detections for Medusa's signature BYOVD pattern — vulnerable driver drops, kernel-level EDR tamper, and the kill-chain that follows.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/Medusa-BYOVD-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/Medusa-BYOVD-Hunt.html)

---

### MimiCRAT Hunt
**Mimikatz-style credential theft + RAT activity**
Hunt for MimiCRAT tradecraft — LSASS access, credential dumping, and the persistent remote-access tooling that ships with it.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/MimiCRAT-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/MimiCRAT-Hunt.html)

---

### NetSupport Manager Hunt
**Abused legitimate RMM / remote access tool**
Hunt pack for Red Canary's NetSupport Manager tracking and related Scarlet Goldfinch, SocGholish, ClickFix, and RMM-abuse delivery chains — covers suspicious `client32.exe` execution, renamed NetSupport binaries, non-standard install paths, attacker-controlled configuration files, persistence, gateway/C2 traffic, Custom IOA guidance, validation gates, and RMM hardening playbooks.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/NetSupportManager-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/NetSupportManager-Hunt.html)

---

### Scarlet Goldfinch Hunt
**ClickFix / SmartApeSG / NetSupport Manager delivery**
Hunt pack for Red Canary's Scarlet Goldfinch tracking and related Blumira, SANS ISC, ThreatDown, Proofpoint, and Team Cymru enrichment - covers fake CAPTCHA and ClickFix lures, cmd delayed-expansion and caret obfuscation, curl/mshta/msiexec/finger/forfiles LOLBAS execution, WMI process creation, persistence, NetSupport Manager and Remcos handoff, IOC handling, Custom IOA guidance, validation gates, hardening, and containment.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/ScarletGoldfinch-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/ScarletGoldfinch-Hunt.html)

---

### PhantomVault Hunt
**Credential-vault / secrets-manager abuse**
Detections for PhantomVault-class attacks against Windows Credential Manager, DPAPI, and browser credential stores.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/PhantomVault-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/PhantomVault-Hunt.html)

---

### PayoutsKing Hunt
**Ransomware / QEMU evasion / remote access and exfiltration**
Behavior-first HuntPack for PayoutsKing ransomware and associated GOLD ENCOUNTER/STAC4713 intrusion tradecraft — covers QEMU-based covert access, suspicious scheduled tasks, Quick Assist and ScreenConnect abuse, AD credential staging, Rclone/SFTP exfiltration, recovery inhibition, Falcon LogScale CQL hunts, Custom IOA candidates, IOC action handling, validation gates, hardening, and containment.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/PayoutsKing-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/PayoutsKing-Hunt.html)

---
### QEMU Hunt
**Living-off-the-land virtualization abuse**
Hunts for QEMU being weaponized for evasion — adversary-controlled VMs used to bypass EDR, hide C2, and stage payloads outside the host's visibility.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/QEMU-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/QEMU-Hunt.html)

---

### SilentCanvas Hunt
**Stealthy browser / Canvas-based fingerprinting & exfil**
Detections for SilentCanvas-style covert-channel activity inside browsers — fingerprinting, sandbox escapes, and data smuggling via rendering APIs.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/SilentCanvas-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/SilentCanvas-Hunt.html)

---

### Tampered Chef Hunt
**Signed fake productivity apps with steganographic / homoglyph command delivery**
Hunt pack for Red Canary's Tampered Chef tracking and adjacent TamperedChef-style malvertising clusters — covers RecipeLister, Calendaromatic, AppSuite-style PDF tools, code-signing pivots, Chrome/search hijacking, suspicious Electron/NeutralinoJS execution, browser credential-store access, persistence, Custom IOA guidance, and hardening playbooks.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/TamperedChef-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/TamperedChef-Hunt.html)

---

### The Gentlemen — Ransomware Hunt
**The Gentlemen ransomware operation**
Hunt pack for The Gentlemen's intrusion set — initial access, lateral movement, defense evasion, and pre-encryption staging behaviors.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/TheGentlemen-RansomwareHunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/TheGentlemen-RansomwareHunt.html)

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
