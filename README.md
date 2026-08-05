[![eugeneivanov.dev — Infrastructure Engineering](assets/eugeneivanov-dev-logo_1280.webp)](https://eugeneivanov.dev)

# Home Infrastructure Lab

A working infrastructure environment I build, operate, and document — networking, Linux, virtualization, high availability, PKI, observability, and configuration management on real hardware.

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

## Hardware

- 2 × Dell Pro Micro Plus (Intel Core Ultra 7, 64 GB RAM, dual NVMe) — cluster nodes
- Synology RS1221+ rack NAS, APC rackmount UPS
- UniFi: Dream Machine Pro Max, Pro Max 24 PoE, Enterprise 8 PoE, 2 × Lite 8 PoE, 2 × U7 Pro
- 12U wall-mounted rack, structured Cat6 cabling, patch panel

Full environment: [eugeneivanov.dev/infra](https://eugeneivanov.dev/infra)

---

## Repositories

### [ansible](https://github.com/eugeneivanov-dev/ansible)
The lab's OS baseline as code. Two fleets — RHEL and Ubuntu — as fleet-prefixed idempotent roles: registration, SSH hardening, SELinux/AppArmor, firewall, time, updates, resolver, monitoring agent. A clean VM reaches the lab standard by playbook alone; existing hosts are drift-checked in check mode. Linted in CI on every push.

Project pages: [Ansible Baseline](https://eugeneivanov.dev/projects/ansible-baseline-for-the-lab/) · [Ubuntu Baseline](https://eugeneivanov.dev/projects/ubuntu-baseline-for-the-lab/)

### [homelab](https://github.com/eugeneivanov-dev/homelab)
The engineering journal — implementation logs, troubleshooting cases, and technical decisions from real lab work. The polished version lives on the website; this repository is the working record.

Published journal: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)  
Raw journal: [journal/README.md](https://github.com/eugeneivanov-dev/homelab/blob/main/journal/README.md)

---

## Recent work

- 2026-08-03 — Auditing the Ubuntu fleet before Ansible touches it
- 2026-08-02 — App services on Let's Encrypt: public certificates for internal names
- 2026-08-02 — Attaching consumers to the internal CA: Proxmox, Synology, and device trust
- 2026-08-02 — Building a private certificate authority with step-ca on RHEL
- 2026-07-31 — Going public: opening the Ansible repo, decisions and mechanics
- 2026-07-28..30 — Ansible Baseline, parts 1–6: from control node to adopting the live fleet
- 2026-07-19 — Internal DNS: BIND primary/secondary on RHEL
- 2026-06-27 — When a node reinstall resurfaced an old NIC hang — and HA caught it
- 2026-06-22 — Two-node Proxmox HA with ZFS replication and a verified failover

Full chronology: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)

---

## Roadmap

1. **Networking Foundations** — core complete, deepening
2. **Linux & Virtualization** — core complete, deepening
3. **Infrastructure Services & Observability** — core complete, expanding (identity and secrets services next)
4. **Automation & Operational Maturity** — baseline in production for both fleets
5. **Resilient Infrastructure, Clustering & Kubernetes** — two-node HA operational; third node and Kubernetes ahead
6. **Systems Architecture** — future

Details: [eugeneivanov.dev/roadmap](https://eugeneivanov.dev/roadmap)

---

## Principles

- Automation after the manual phase, not instead of it — codifying a process you don't fully understand encodes the misunderstanding
- Recovery is proven, not assumed — every backup layer restore-tested, failover verified by pulling power
- Redundancy matched to the service — DNS fails over by protocol, most services by hypervisor HA; the failure mode picks the tool
- Documentation is part of the work — decisions captured while the context is still fresh

---

## Links

- **Website:** [eugeneivanov.dev](https://eugeneivanov.dev)
- **Infrastructure:** [eugeneivanov.dev/infra](https://eugeneivanov.dev/infra)
- **Roadmap:** [eugeneivanov.dev/roadmap](https://eugeneivanov.dev/roadmap)
- **Journal:** [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)
- **LinkedIn:** [linkedin.com/in/eugeneivanov-dev](https://www.linkedin.com/in/eugeneivanov-dev)