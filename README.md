# HuntPack

> A growing collection of CrowdStrike CQL threat-hunting packs — each one a self-contained HTML report with the hunt hypothesis, MITRE mapping, copy-paste CQL queries, triage checklist, and hardening guidance.

Every file in this repo is a standalone HTML report. Use the **Preview** link to render it in your browser via [htmlpreview.github.io](https://htmlpreview.github.io), or the **Source** link to view the raw file on GitHub.

---

## Hunts

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

### DirtyFrag Hunt
**Active Directory fragmentation / Kerberos abuse**
Hunts for DirtyFrag-class AD exploitation — ticket manipulation, certificate abuse, and post-exploit privilege escalation patterns.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/DirtyFrag-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/DirtyFrag-Hunt.html)

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

### PhantomVault Hunt
**Credential-vault / secrets-manager abuse**
Detections for PhantomVault-class attacks against Windows Credential Manager, DPAPI, and browser credential stores.

[Preview](https://htmlpreview.github.io/?https://github.com/slapopotamus/HuntPack/blob/main/PhantomVault-Hunt.html) · [Source](https://github.com/slapopotamus/HuntPack/blob/main/PhantomVault-Hunt.html)

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

## Contributing

Hunts live as single-file HTML reports so they're easy to share, version, and preview without a build step. PRs welcome.

## License

See repository.
