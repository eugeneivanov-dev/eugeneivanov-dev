[![eugeneivanov.dev — Infrastructure Engineering](assets/eugeneivanov-dev-logo_1280.webp)](https://eugeneivanov.dev)

# Infrastructure Lab

A working infrastructure environment I build, operate, and document — networking, Linux, virtualization, high availability, PKI, observability, and configuration management on real hardware. This lab is the engineering base behind [Proven Infrastructure Group](https://proveninfra.com): methods are rehearsed here before they touch client production.

**Website:** [eugeneivanov.dev](https://eugeneivanov.dev)

---

## What's running

- Proxmox VE two-node HA cluster on ZFS — bidirectional replication, external QDevice for quorum, watchdog fencing, failover verified by a hard power-off test
- RHEL 10 and Ubuntu Server fleet, managed by Ansible ([public repo](https://github.com/eugeneivanov-dev/ansible)) — idempotent roles, lint CI, drift checks
- Internal DNS on BIND 9 — primary/secondary on separate nodes, forward and reverse zones
- Two certificate authorities, split by consumer class — private PKI on step-ca for management interfaces, Let's Encrypt over DNS-01 for internal web services
- Prometheus and Grafana with Node, Blackbox, and PVE exporters — dashboards, alert rules, SMTP notifications
- Seven VLANs with deny-by-default inter-VLAN firewall policy; WireGuard, Tailscale, and Cloudflare Tunnel for remote access
- Off-node backups (Proxmox vzdump) and logical database dumps, both verified by real restores
- Self-hosted services on Docker Compose: analytics, newsletter, internal tooling

Next up: identity and secrets services — FreeIPA, Keycloak, HashiCorp Vault.

## Hardware

- 2 × Dell Pro Micro Plus (Intel Core Ultra 7, 64 GB RAM, dual NVMe) — cluster nodes
- Synology DS720+ NAS (backup target, QDevice); RS1221+ rack NAS (not yet in service)
- APC rackmount UPS
- UniFi: Dream Machine Pro Max, Pro Max 24 PoE, Enterprise 8 PoE, 2 × Lite 8 PoE, 2 × U7 Pro
- 12U wall-mounted rack, structured Cat6 cabling, patch panel

Full environment: [eugeneivanov.dev/infra](https://eugeneivanov.dev/infra)

---

## Repositories

### [ansible](https://github.com/eugeneivanov-dev/ansible)
The lab's OS baseline as code. Two fleets — RHEL and Ubuntu — as fleet-prefixed idempotent roles: registration, SSH hardening, SELinux/AppArmor, firewall, time, updates, resolver, monitoring agent. A clean VM reaches the lab standard by playbook alone; existing hosts are drift-checked in check mode. Linted in CI on every push.

Project pages: [Ansible Baseline](https://eugeneivanov.dev/projects/ansible-baseline-for-the-lab/) · [Ubuntu Baseline](https://eugeneivanov.dev/projects/ubuntu-baseline-for-the-lab/)

### [infralab](https://github.com/eugeneivanov-dev/infralab)
The engineering journal — implementation logs, troubleshooting cases, and technical decisions from real lab work. The polished version lives on the website; this repository is the working record.

Published journal: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)  
Raw journal: [journal/README.md](https://github.com/eugeneivanov-dev/infralab/blob/main/journal/README.md)

---

## Recent work

- 2026-08-19 — Hugo on Cloudways: CI/CD with GitHub Actions
- 2026-08-12 — Adopting a live Ubuntu fleet with Ansible: changed=0 across twelve hosts of both fleets
- 2026-08-11 — Proving the Ansible baseline on a clean Ubuntu VM — and catching a real sshd bug the incremental path never could
- 2026-08-10 — Writing Ansible roles for an Ubuntu Server baseline: fleet-prefixed roles, idempotency proven
- 2026-08-03 — Auditing the Ubuntu fleet before Ansible touches it
- 2026-08-02 — App services on Let's Encrypt: public certificates for internal names
- 2026-08-02 — Attaching consumers to the internal CA: Proxmox, Synology, and device trust
- 2026-08-02 — Building a private certificate authority with step-ca on RHEL
- 2026-07-31 — Going public: opening the Ansible repo, decisions and mechanics
- 2026-07-28..30 — Ansible Baseline, parts 1–6: from control node to adopting the live fleet

Full chronology: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)

---

## Principles

- Automation after the manual phase, not instead of it — codifying a process you don't fully understand encodes the misunderstanding
- Recovery is proven, not assumed — every backup layer restore-tested, failover verified by pulling power
- Redundancy matched to the service — DNS fails over by protocol, most services by hypervisor HA; the failure mode picks the tool
- Documentation is part of the work — decisions captured while the context is still fresh
