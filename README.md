<picture>
  <source media="(prefers-color-scheme: dark)" srcset="dark_mode.svg" />
  <source media="(prefers-color-scheme: light)" srcset="light_mode.svg" />
  <img alt="Egyan07's GitHub profile" src="dark_mode.svg" width="100%" />
</picture>

<div align="center">

<a href="https://github.com/Egyan07">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:0f3460,100:533483&height=160&section=header&text=EGYAN&fontSize=64&fontColor=ffffff&fontAlignY=42&desc=Security%20engineering%20%2B%20automation&descSize=16&descAlignY=62" alt="Header" />
</a>

</div>

### About

I build and ship security and automation tooling: compliance scoring, encrypted backups, threat intelligence, TLS fingerprinting, Active Directory attack detection. Design, implementation, testing, and packaging are all mine.

My degree is in Business Management. The engineering is self-taught, built by shipping full projects rather than following a course.

Day job: IT & self-assessment at Red Parrot Accounting (UK). Four of the tools below were built for use there and are noted as such; the rest are independent projects.

---

## Selected Projects

**[ComplianceGuard](https://github.com/Egyan07/ComplianceGuard)** — `v3.7.0`
Endpoint compliance automation, scoring SOC 2 (54 controls), ISO 27001 (47), HIPAA (47), and GDPR (38) from evidence collected directly off Windows/macOS machines — not just cloud config. Desktop app (Electron) or self-hosted Docker deployment, Ed25519-signed licensing, tiered pricing. I built the scoring engine, evidence-collection pipeline, desktop packaging, and reporting. Backend: 359 tests (315 unit, 35 integration, 9 e2e); frontend: 235 unit tests.
`FastAPI` `React` `TypeScript` `Electron` `PostgreSQL`

**[GhostBackup](https://github.com/Egyan07/GhostBackup)** — deployed at Red Parrot Accounting (UK)
Streaming encrypted backups using AES-256-GCM. Delta detection means only changed data gets re-encrypted and copied to dual local SSDs; a restore-verification step and startup self-check confirm backups are actually recoverable, not just present. 744 tests (backend, frontend, Electron), all passing, ~90% backend coverage.
`Python` `FastAPI` `Electron` `SQLite`

**[PhantomEye](https://github.com/Egyan07/PhantomEye)** — `v2.1`
Threat intelligence tool with zero runtime dependencies — stdlib only. Pulls 40,000+ IOCs from 8 OSINT feeds into a structure built for O(1) lookup, then scans firewall logs, DNS cache, and email headers against it. 222+ tests, including a dedicated 18-test input-validation suite.
`Python` `SQLite` `CodeQL SAST`

**[GhostSecure](https://github.com/Egyan07/GhostSecure)** — `v2.1.2`, built for Red Parrot Accounting Ltd
Windows service watching the Security Event Log for 8 live Active Directory attack techniques in real time — Kerberoasting, Pass-the-Hash, DCSync, Golden Ticket, LDAP recon, AS-REP roasting, Skeleton Key, and audit-log tampering — each mapped to a specific Windows Event ID. 53 tests across all 7 detector modules.
`Python` `pywin32` `Windows Service`

**[ViperFin](https://github.com/Egyan07/ViperFin)** — `v1.1.1`
JA3/JA3S TLS fingerprinting, written in Go, stdlib only. Parses the raw ClientHello to identify what's making a TLS connection — browser, scanner, or malware C2 (Cobalt Strike, Emotet, TrickBot) — with RFC 8701 GREASE filtering so randomized values don't break the fingerprint. Cross-compiles for Linux, Windows, and macOS.
`Go` `TLS`

**Also:** [VaultSentry](https://github.com/Egyan07/VaultSentry) — backup integrity monitoring for Red Parrot Accounting, using SHA-256 hashing and Shannon-entropy analysis to flag likely ransomware encryption, plus snapshot diffing and a restore engine. 162 tests, 73% coverage.

---

## Stack

**Languages** — Python · Go · TypeScript · JavaScript · C · PowerShell

**Backend** — FastAPI · PostgreSQL · SQLite · Docker · Nginx

**Desktop / Frontend** — Electron · React · Vite · Tailwind

**Security** — TLS fingerprinting · Ed25519 / AES-256-GCM · Windows internals (AD, registry) · threat intelligence

**Testing / CI** — pytest · CodeQL

<div align="center">
<img width="480" src="https://github-readme-stats-sigma-five.vercel.app/api/top-langs/?username=Egyan07&layout=compact&bg_color=0d1117&text_color=c9d1d9&title_color=58a6ff&hide_border=true" alt="Top languages" />
</div>

---

## How I work

- If it's not tested, I don't trust it.
- I build the attack and the detector — understanding one means understanding the other.
- stdlib first; every added dependency is a supply chain decision.
- Document what the tool doesn't do, not just what it does.

---

## Currently exploring

- Hardening Electron apps: process isolation, CSP, update signing, sandbox escapes
- Offline-first licensing that doesn't phone home
- Porting Windows-first security tooling to macOS/Linux without losing depth

---

<div align="center">

[![GitHub](https://img.shields.io/badge/github.com%2FEgyan07-0d1117?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Egyan07)
&nbsp;
[![Email](https://img.shields.io/badge/alexisegyan1232@gmail.com-0d1117?style=for-the-badge&logo=gmail&logoColor=white)](mailto:alexisegyan1232@gmail.com)
&nbsp;
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0d1117?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/egyan07)

</div>
