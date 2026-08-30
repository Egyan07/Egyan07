<picture>
  <source media="(prefers-color-scheme: dark)" srcset="dark_mode.svg" />
  <source media="(prefers-color-scheme: light)" srcset="light_mode.svg" />
  <img alt="Egyan07's GitHub profile" src="dark_mode.svg" width="100%" />
</picture>

Most of what I build lives below the API layer: parsing raw TLS handshakes, watching Windows Event Logs for attack patterns, streaming encrypted backups byte by byte, scoring compliance evidence pulled directly off a machine instead of a policy checklist. I handle the design, implementation, testing, and packaging.

My degree is in Business Management. My engineering background is self-taught, mostly through building and shipping full projects: parsers, services, detection engines, and desktop applications. What's below is what came out of that.

**What I build**
- Security tooling that reads raw protocol and log data directly, not through someone else's SDK
- Backend services and desktop apps (FastAPI + Electron/React)
- Detection and threat-intelligence systems
- Compliance automation and cryptographic/backup infrastructure

Day job: IT & self-assessment at Red Parrot Accounting (UK). Four of the projects below were built for use there and are noted as such; the rest are independent.

---

## Featured

**[ComplianceGuard](https://github.com/Egyan07/ComplianceGuard)** · `v3.8.1`
Compliance automation that scores evidence collected directly off a Windows or macOS machine, not a cloud config screen.

It checks a real endpoint against SOC 2 (54 controls), ISO 27001 (47), HIPAA (47), and GDPR (38), and ships either as an Electron desktop app or a self-hosted Docker deployment. The part I found genuinely hard: building an Ed25519-signed licensing system for software distributed outside an app store, where you can't lean on a platform to handle activation for you. I built the scoring engine, the evidence-collection pipeline, the desktop packaging, and the reporting layer. Backend: 359 tests (315 unit, 35 integration, 9 e2e). Frontend: 235 unit tests.

`FastAPI` `React` `TypeScript` `Electron` `PostgreSQL`

**[GhostBackup](https://github.com/Egyan07/GhostBackup)** · deployed at Red Parrot Accounting, UK
Streaming, AES-256-GCM authenticated encryption for backups, with the assumption baked in that a backup that finishes isn't necessarily a backup that works.

Delta detection means only changed data gets re-encrypted and copied across, rather than re-processing everything on every run. A restore-verification step and a startup self-check exist specifically to catch the failure mode most backup tools ignore: silent corruption you don't discover until the day you actually need the backup. 744 tests across backend, frontend, and the Electron shell, all passing, roughly 90% backend coverage.

`Python` `FastAPI` `Electron` `SQLite`

**[PhantomEye](https://github.com/Egyan07/PhantomEye)** · `v2.1`
A threat-intelligence lookup engine built to answer one question fast: is this IP, domain, or hash something we already know about.

40,000+ IOCs pulled from 8 OSINT feeds, loaded into a structure built for O(1) lookup, then matched against firewall logs, DNS cache entries, and email headers. No runtime dependencies outside the standard library. 222+ tests, including an 18-test suite dedicated just to input validation.

`Python` `SQLite` `CodeQL SAST`

**[GhostSecure](https://github.com/Egyan07/GhostSecure)** · `v2.1.2`, built for Red Parrot Accounting Ltd
A Windows service that watches the Security Event Log as it's written, looking for eight specific Active Directory attack techniques: Kerberoasting, Pass-the-Hash, DCSync, Golden Ticket, LDAP recon, AS-REP roasting, Skeleton Key use, and audit-log tampering.

Each detector maps to a specific Windows Event ID rather than scoring a generic anomaly, which is the difference between an alert someone can act on and one they learn to ignore. Eight attack techniques across seven detector modules (one module handles both Skeleton Key use and audit-log tampering), with 53 tests covering the detection logic.

`Python` `pywin32` `Windows Service`

---

## More work

**[ViperFin](https://github.com/Egyan07/ViperFin)** · `v1.1.1`
JA3/JA3S TLS fingerprinting written in Go. Parses the raw ClientHello bytes off the wire to identify what's actually making a TLS connection, a browser, a scanner, or malware C2 like Cobalt Strike, Emotet, or TrickBot, with RFC 8701 GREASE filtering so randomized cipher values don't produce false fingerprints. Cross-compiles for Linux, Windows, and macOS with no non-stdlib dependencies.
`Go` `TLS`

**[VaultSentry](https://github.com/Egyan07/VaultSentry)**, built for Red Parrot Accounting
Backup integrity monitoring using SHA-256 hashing and Shannon-entropy analysis to flag the kind of high-entropy rewrite pattern ransomware leaves behind, plus snapshot diffing and a restore engine. 162 tests, 73% coverage.
`Python` `SQLite`

---

## Stack

**Languages:** Python, Go, TypeScript, JavaScript, C, PowerShell
**Backend:** FastAPI, PostgreSQL, SQLite, Docker, Nginx
**Desktop / Frontend:** Electron, React, Vite, Tailwind
**Security:** TLS fingerprinting, Ed25519, AES-256-GCM, Windows internals (AD, registry), threat intelligence
**Testing / CI:** pytest, CodeQL

---

## How I work

- If it's not tested, I don't trust it in production.
- I build the attack technique and the detector for it, in that order, so I know the detector actually catches something real.
- Standard library first. Every dependency added after that is a decision I have to justify.
- A tool's docs should say what it doesn't handle, not just what it does.

---

## Currently exploring

- Sandboxing Electron's renderer process without breaking the native OS integrations ComplianceGuard depends on
- Licensing that verifies offline, with no phone-home call required at launch
- Porting GhostSecure's detection logic to Linux auditd and macOS unified logging without losing the fidelity the Windows Event Log gives it

---

Each repository README documents its own architecture, test setup, and changelog, worth a look if a project above catches your eye.

Open to: security engineering · backend engineering · security tooling

**Contact:** [GitHub](https://github.com/Egyan07) · [Email](mailto:alexisegyan1232@gmail.com) · [LinkedIn](https://linkedin.com/in/egyan07)
