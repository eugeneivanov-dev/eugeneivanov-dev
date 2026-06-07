[![eugeneivanov.dev — Infrastructure Engineering](assets/eugeneivanov-dev-logo_1280.webp)](https://eugeneivanov.dev)

# Home Infrastructure Lab

A hands-on infrastructure lab where I build, operate, and document real systems — networking, Linux, virtualization, observability, and methodical troubleshooting on real hardware.

This repository documents the lab end-to-end: architecture, implementation logs, technical decisions, troubleshooting cases, and engineering notes from real work.

**Website:** [eugeneivanov.dev](https://eugeneivanov.dev)

---

## Overview

The lab is the practical foundation behind a longer engineering path — a place to develop hands-on skills, document them honestly, and extend them as experience grows. The focus is on building, operating, and improving a real environment over time, not on isolated experiments.

The long-term direction moves through networking depth, Linux and virtualization, infrastructure services and observability, operational maturity, resilience, and system-level design — laid out in the [roadmap](https://eugeneivanov.dev/roadmap).

---

## Current Focus

Right now the work centers on three things: networking depth (CCNA in progress), continuing to expand and refine the observability stack, and preparing the next layer of services — internal DNS, NetBox as a source of truth, and self-hosted VPN through WireGuard.

The broader phase remains *Infrastructure Services and Observability* — the core is operational, and the work is extending it.

---

## Repositories

### homelab — Engineering Journal
The main public repository for this work. Contains a working engineering journal — implementation logs, troubleshooting notes, and technical decisions captured during real lab work. The polished, published version of the journal lives on the website; this repository is the working record.

Repository: [github.com/eugeneivanov-dev/homelab](https://github.com/eugeneivanov-dev/homelab)  
Published journal: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)  
Published RAW journal: [github.com/eugeneivanov-dev/homelabl/journal/readme.md](https://github.com/eugeneivanov-dev/homelab/journal/README.md)

### networking-labs — Networking Experiments (Early Stage)
A separate repository scoped for hands-on networking exercises — DNS, VLAN segmentation, VPN, firewall configuration, and network troubleshooting. Currently early-stage, with active development planned alongside CCNA preparation.

Repository: [github.com/eugeneivanov-dev/networking-labs](https://github.com/eugeneivanov-dev/networking-labs)

---

## Infrastructure Stack

The physical and virtual environment behind the work documented here — actively running, not theoretical.

### Network

- UniFi Dream Machine Pro Max (gateway and firewall)
- UniFi Pro Max 24 PoE (core switch)
- UniFi Enterprise 8 PoE (10G uplink)
- 2 × UniFi Lite 8 PoE (distribution)
- 2 × UniFi U7 Pro access points

### Compute and storage

- Dell Pro Micro Plus — Intel Core Ultra 7, 64 GB RAM, 1 TB + 2 TB NVMe (Proxmox VE node)
- Synology RS1221+ (rack-mounted NAS, backup and storage)
- APC rack-mounted UPS
- 12U wall-mounted rack with structured Ethernet cabling and patch panel

### Platform layer

- Proxmox VE virtualization with multiple Ubuntu Server VMs
- Docker Compose for self-hosted services (Umami, Plausible, Matomo, internal tooling)
- Tailscale VPN and Cloudflare Tunnel for secure remote access
- Prometheus, Grafana, Node Exporter, Blackbox Exporter, and Proxmox PVE Exporter
- VLAN-based network segmentation across Main, IoT, Guest, Lab, and Quarantine
- macOS and Windows administrative environments

Infrastructure documentation: [eugeneivanov.dev/infra](https://eugeneivanov.dev/infra)

---

## Architecture

### Current

Single-node Proxmox foundation running multiple Linux VMs, with VLAN-segmented UniFi networking, centralized NAS storage, rack-mounted power protection, and a monitoring layer covering VMs, HTTP services, and Proxmox infrastructure. Secure remote access through Tailscale and Cloudflare Tunnel. Operational workflows and troubleshooting documented as part of the work.

### Planned Evolution

- Expansion from 1 Proxmox node to 3 nodes for high availability
- Deeper NAS integration as shared storage for the cluster
- Stronger backup, restore, and recovery validation procedures
- Automation through Ansible, then infrastructure-as-code with Terraform
- Cloud integration once the on-prem foundation is mature
- Kubernetes only after clustering and resilience foundations are in place

---

## Roadmap

The work in this lab follows a phased infrastructure engineering roadmap. Each phase has an honest status — what is operational, what is deepening, what is still ahead.

1. **Networking Foundations** — *Core complete · deepening (CCNA in progress)*
2. **Linux & Virtualization** — *Core complete · deepening (RHCSA ahead)*
3. **Infrastructure Services & Observability** — *Core complete · expanding*
4. **Automation & Operational Maturity** — *In progress*
5. **Resilient Infrastructure, Clustering & Kubernetes** — *Future*
6. **Systems Architecture** — *Future*

Full roadmap with details, principles, and certifications: [eugeneivanov.dev/roadmap](https://eugeneivanov.dev/roadmap)

---

## Current Status

### Phase status

- **Networking Foundations** — core complete, deepening through CCNA
- **Linux & Virtualization** — core complete, deepening alongside RHCSA preparation
- **Infrastructure Services & Observability** — core complete, expanding coverage and refining behavior
- **Automation & Operational Maturity** — in progress

### What this means in practice

Recent and near-term work centers on extending the observability stack (new metrics, sharper alert thresholds, validated failure paths), preparing the next service layer (internal DNS, NetBox as a source of truth, self-hosted VPN through WireGuard), and beginning the move from manual workflows to repeatable ones — light automation today, Ansible next.

---

## Engineering Log

> Recent infrastructure work:

- 2026-06-06 - Fixing a Phantom “Unknown Error” on a Cisco 8861 MPP Phone
- 2026-06-05 - Self-hosted newsletter is live
- 2026-06-01 - Self-Hosted Website Audits with SiteOne Crawler and systemd
- 2026-05-31 - Improved Proxmox Grafana dashboard readability
- 2026-05-25 — Resolved recurring GitHub SSH authentication prompts
- 2026-05-22 — Upgraded Proxmox VE from 9.1 to 9.2.2 with documented validation
- 2026-05-20 — Built a cross-platform Unity workspace for a beginner C# programmer
- 2026-05-12 — Investigated noisy Grafana memory alerts and tuned the Proxmox memory threshold
- 2026-05-11 — Published the self-hosted observability stack overview
- 2026-05-11 — Configured Grafana alert rules with Proton SMTP email notifications
- 2026-05-11 — Organized Grafana dashboards by layer (VMs, services, Proxmox)
- 2026-05-10 — Added Node, Blackbox, and PVE exporters covering Linux VMs, HTTP services, and Proxmox infrastructure
- 2026-05-09 — Deployed Prometheus and Grafana on a dedicated monitoring VM
- 2026-05-09 — Prepared a reusable Ubuntu Server VM baseline for Docker infrastructure

Full chronology of journal entries, troubleshooting cases, and lab notes: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)

---

## Certification Direction

Certifications are treated as checkpoints along the work, not the work itself. Each one validates real practice rather than driving it.

- **CCNA** — in progress (Cisco Networking Academy)
- **RHCSA** — next, alongside continued Linux administration depth
- **CKA** — later, only after clustering and Kubernetes work is real
- **One cloud certification** — only if it becomes directly relevant to real work

---

## Core Reading Library

Books support the long-term foundation behind this lab. They deepen understanding over time but do not replace real implementation, troubleshooting, or documentation.

### Currently reading

- *CCNA 200-301 Official Cert Guide, Volume 1&2*, 2nd Edition — Wendell Odom
- *CCNA 200-301 Hands-on Mastery with Packet Tracer* — Sequeira & Wong
- *Acing the CCNA Exam, Volume 1&2* — Jeremy McDowell
- *31 Days Before Your CCNA Exam*

### On the shelf (long-term reading path)

- *Computer Networking: A Top-Down Approach* — Kurose & Ross
- *TCP/IP Illustrated, Volume 1* — Fall & Stevens
- *UNIX and Linux System Administration Handbook* — Nemeth et al.
- *The Practice of System and Network Administration* — Limoncelli et al.
- *Site Reliability Engineering* — Google
- *The Site Reliability Workbook* — Google
- *Building Secure and Reliable Systems* — Google
- *Designing Data-Intensive Applications* — Martin Kleppmann
- *The Pragmatic Programmer*
- *Pro Git*
- *Linux Bible*
- *Automate the Boring Stuff with Python* — Al Sweigart
- *The Linux Command Line* — William Shotts
- *Practical Packet Analysis* — Chris Sanders

---

## Philosophy

**Working principle:**  
be current · do the work · document the process.

The best way to understand infrastructure is to build, operate, break, and repair real systems — then write down what happened. Theory matters, but understanding is built through implementation, troubleshooting, and the discipline of documenting decisions while they are still fresh.

The goal is not only to make systems work, but to understand how they are organized, how they behave, how they fail, and how they improve over time.

---

## Key Decisions

- **Built physical infrastructure first** — rack, structured cabling, patch panel, and UPS from day one, so everything above the physical layer sits on a stable foundation
- **Chose Proxmox VE as the virtualization platform** — open-source, snapshots and backups out of the box, single pane for VMs and storage, and a clear path to clustering when the time comes
- **Started with a single capable compute node** — Dell Pro Micro Plus with Intel Ultra 7, 64 GB RAM, and dual NVMe — strong enough to host real workloads now, modular enough to grow into a 3-node cluster later
- **Standardized on UniFi for the network stack** — consistent management, integrated VLANs and firewall policy, room to grow without changing vendors mid-build
- **Designed VLAN segmentation with five separate networks** — including a Quarantine VLAN for unknown or untrusted devices, treating segmentation as boundaries of trust, not just address ranges
- **Built secure remote access through Tailscale and Cloudflare Tunnel** — no open inbound ports on the home network, role-based access through ACLs
- **Treated documentation as part of the work, not after it** — every meaningful change captured in the engineering journal while the context is still fresh

---

## Links

- **Website:** [eugeneivanov.dev](https://eugeneivanov.dev)
- **Infrastructure:** [eugeneivanov.dev/infra](https://eugeneivanov.dev/infra)
- **Roadmap:** [eugeneivanov.dev/roadmap](https://eugeneivanov.dev/roadmap)
- **Journal:** [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)
- **LinkedIn:** [linkedin.com/in/eugeneivanov-dev](https://www.linkedin.com/in/eugeneivanov-dev)
- **Home Lab Repository:** [github.com/eugeneivanov-dev/homelab](https://github.com/eugeneivanov-dev/homelab)
- **Networking Labs Repository:** [github.com/eugeneivanov-dev/networking-labs](https://github.com/eugeneivanov-dev/networking-labs)