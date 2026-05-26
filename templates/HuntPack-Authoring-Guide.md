# HuntPack Authoring Guide

Use `HuntPack-Template.html` as the starting point for each future hunt pack. The template is intentionally single-file HTML so it can be committed to GitHub and previewed without a build step.

## Fast Start

1. Copy `HuntPack-Template.html` and rename it as `<ThreatName>-Hunt.html`.
2. Replace every `{{PLACEHOLDER}}`.
3. Run a web-hunter pass against primary reporting, vendor research, public malware-lab writeups, ATT&CK/LOLBAS references, and IOC sources.
4. Keep high-confidence blockable IOCs separate from broad pivots and enrichment strings.
5. Validate every CQL query over a short time window before publishing.
6. Fill out the validation gates, telemetry gaps, containment runbook, changelog, and references before sharing externally.

## Recommended Creation Order

1. Executive summary
2. Source review and web-hunter notes
3. Threat brief and attack chain
4. IOC table and machine-readable IOC appendix
5. Telemetry matrix and native audit-log hunts
6. ATT&CK mapping
7. CQL query cards
8. Custom IOA candidates
9. Validation gates
10. Hardening and deployable playbooks
11. Containment runbook, coverage map, ticket, changelog, references

## Quality Gates

- Each query has a hypothesis, confidence, false-positive expectation, cost estimate, and required telemetry.
- The source review separates primary sources, corroborating vendor research, community/lab writeups, and weak aggregator-only claims.
- Query field names have been checked against the target tenant or clearly marked as schema-dependent.
- Native audit-log hunts are included when endpoint telemetry cannot see the control-plane action.
- IOCs have confidence, action, source, and expiry or review date.
- Hardening steps are split into immediate, near-term, and strategic actions.
- References include access dates and distinguish primary reporting from community enrichment.
- No threat-specific placeholder remains before publishing.

## Naming

Use short, stable filenames:

```text
ThreatName-Hunt.html
ThreatName-CloudHunt.html
ThreatName-RansomwareHunt.html
ThreatName-SupplyChainHunt.html
```

## GitHub Preview Pattern

After committing the file, preview it with:

```text
https://htmlpreview.github.io/?https://github.com/<owner>/<repo>/blob/<branch>/<ThreatName>-Hunt.html
```

## Source Note

This template follows the repeatable HuntPack pattern from `slapopotamus/HuntPack`: single-file HTML reports with hunt hypothesis, MITRE mapping, CQL queries, triage/validation guidance, hardening, containment, and references. It does not copy threat-specific text from any existing pack.
