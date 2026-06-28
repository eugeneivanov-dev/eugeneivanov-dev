[![eugeneivanov.dev — Infrastructure Engineering](assets/eugeneivanov-dev-logo_1280.webp)](https://eugeneivanov.dev)

# Home Infrastructure Lab

A hands-on infrastructure lab where I build, operate, and document real systems — networking, Linux, virtualization, high availability, observability, and methodical troubleshooting on real hardware.

This repository documents the lab end-to-end: architecture, implementation logs, technical decisions, troubleshooting cases, and engineering notes from real work.

**Website:** [eugeneivanov.dev](https://eugeneivanov.dev)

---

## Overview

The lab is the practical foundation behind a longer engineering path — a place to develop hands-on skills, document them honestly, and extend them as experience grows. The focus is on building, operating, and improving a real environment over time, not on isolated experiments.

The long-term direction moves through networking depth, Linux and virtualization, infrastructure services and observability, operational maturity, resilience, and system-level design — laid out in the [roadmap](https://eugeneivanov.dev/roadmap).

---

## Current Focus

Right now the work centers on: Linux administration depth (RHCSA in progress), operating and refining the two-node high-availability cluster, continuing to expand the observability stack, and preparing the next service layer — internal DNS and NetBox as a source of truth.

The broader phase remains *Infrastructure Services and Observability* — the core is operational, and the work is extending it.

---

## Repositories

### homelab — Engineering Journal
The main public repository for this work. Contains a working engineering journal — implementation logs, troubleshooting notes, and technical decisions captured during real lab work. The polished, published version of the journal lives on the website; this repository is the working record.

Repository: [github.com/eugeneivanov-dev/homelab](https://github.com/eugeneivanov-dev/homelab)  
Published journal: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)  
Published RAW journal: [github.com/eugeneivanov-dev/homelab/journal/README.md](https://github.com/eugeneivanov-dev/homelab/blob/main/journal/README.md)

### networking-labs — Networking Experiments (Early Stage)
A separate repository scoped for hands-on networking exercises — DNS, VLAN segmentation, VPN, firewall configuration, and network troubleshooting. Currently early-stage, with active development planned alongside continued networking depth.

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

- 2 × Dell Pro Micro Plus — Intel Core Ultra 7, 64 GB RAM, 1 TB + 2 TB NVMe each (Proxmox VE cluster nodes)
- Synology RS1221+ (rack-mounted NAS — off-node backups and storage)
- APC rack-mounted UPS
- 12U wall-mounted rack with structured Ethernet cabling and patch panel

### Platform layer

- Proxmox VE two-node high-availability cluster on ZFS, with bidirectional replication and watchdog fencing
- External QDevice (corosync-qnetd) on Synology as a third quorum vote
- RHEL 10 and Ubuntu Server VMs
- Docker Compose for self-hosted services (Umami, Plausible, Matomo, Listmonk, internal tooling)
- WireGuard (deny-by-default), Tailscale, and Cloudflare Tunnel for secure remote access
- Prometheus, Grafana, Node Exporter, Blackbox Exporter, and Proxmox PVE Exporter
- Off-node backups (Proxmox vzdump) and logical database dumps, verified by restore
- VLAN-based network segmentation across Main, Lab, Camera, IoT, Guest, Default, and Quarantine
- macOS and Windows administrative environments

Infrastructure documentation: [eugeneivanov.dev/infra](https://eugeneivanov.dev/infra)

---

## Architecture

### Current

Two-node Proxmox VE high-availability cluster on ZFS with bidirectional replication and an external QDevice for quorum, running RHEL 10 and Ubuntu VMs. VLAN-segmented UniFi networking, centralized NAS storage, rack-mounted power protection, and a monitoring layer covering VMs, HTTP services, and Proxmox infrastructure. Off-node backups verified by real restores. Secure remote access through WireGuard, Tailscale, and Cloudflare Tunnel. Operational workflows and troubleshooting documented as part of the work.

### Planned Evolution

- Expansion from two Proxmox nodes to three for native quorum, retiring the external QDevice and enabling HA anti-affinity
- A dedicated Proxmox Backup Server on the rack NAS as the long-term backup home
- Capping the ZFS ARC once a heavier guest set makes the failover RAM budget tight
- Automation through Ansible, then infrastructure-as-code with Terraform
- Cloud integration once the on-prem foundation is mature
- Kubernetes only after clustering and resilience foundations are in place

---

## Roadmap

The work in this lab follows a phased infrastructure engineering roadmap. Each phase has an honest status — what is operational, what is deepening, what is still ahead.

1. **Networking Foundations** — *Core complete · deepening*
2. **Linux & Virtualization** — *Core complete · deepening (RHCSA in progress)*
3. **Infrastructure Services & Observability** — *Core complete · expanding*
4. **Automation & Operational Maturity** — *Early · in progress*
5. **Resilient Infrastructure, Clustering & Kubernetes** — *Clustering & HA operational (two-node) · third node and Kubernetes ahead*
6. **Systems Architecture** — *Future*

Full roadmap with details, principles, and certifications: [eugeneivanov.dev/roadmap](https://eugeneivanov.dev/roadmap)

---

## Current Status

### Phase status

- **Networking Foundations** — core complete, deepening
- **Linux & Virtualization** — core complete, deepening alongside RHCSA preparation
- **Infrastructure Services & Observability** — core complete, expanding coverage and refining behavior
- **Automation & Operational Maturity** — early, in progress
- **Resilient Infrastructure & Clustering** — two-node HA cluster operational; third node and Kubernetes ahead

### What this means in practice

Recent work rebuilt the compute layer from a single node into a two-node high-availability cluster on ZFS replication — with an external QDevice for quorum, off-node backups and a logical database-dump layer both verified by restore, a live in-place node rebuild without downtime, and a hard power-off failover test that proved automatic recovery. Near-term work centers on extending the observability stack, preparing the next service layer (internal DNS, NetBox as a source of truth), and beginning the move from manual workflows to repeatable ones — light automation today, Ansible next.

---

## Engineering Log

> Recent infrastructure work:

- 2026-06-27 — When a node reinstall resurfaced an old NIC hang — and HA caught it
- 2026-06-25 — Deny-by-default WireGuard server on RHEL 10 with firewalld policies
- 2026-06-24 — Built a reusable RHEL 10 baseline for homelab services
- 2026-06-22 — Two-node Proxmox HA with ZFS replication and a verified failover
- 2026-06-22 — Routed Proxmox notifications and system mail through an authenticated relay (SPF/DMARC)
- 2026-06-21 — In-place reinstall of a live cluster node without losing quorum
- 2026-06-21 — Live-migrated VMs from LVM-thin to ZFS, and the thin-provisioning trap
- 2026-06-20 — A Cat6 run stuck at 100 Mbps: the crimper, not the cable
- 2026-06-20 — Backed up Plausible (PostgreSQL + ClickHouse) to the NAS, restore-verified
- 2026-06-15 — Off-node Proxmox backups to Synology, verified by restore
- 2026-06-15 — Independent, restore-tested database-dump layer (PostgreSQL, MariaDB, ClickHouse)
- 2026-06-15 — External Proxmox QDevice on Synology with a corosync-qnetd container
- 2026-06-14 — Formed the two-node cluster (FQDN, storage.cfg), bootable ZFS mirror on mismatched NVMe, Dell node prep
- 2026-06-08 — New-subscriber email notifications for self-hosted Listmonk
- 2026-06-06 — Fixing a phantom "Unknown Error" on a Cisco 8861 MPP phone
- 2026-06-05 — Self-hosted newsletter is live
- 2026-06-01 — Self-hosted website audits with SiteOne Crawler and systemd
- 2026-05-31 — Improved Proxmox Grafana dashboard readability
- 2026-05-25 — Resolved recurring GitHub SSH authentication prompts
- 2026-05-22 — Upgraded Proxmox VE from 9.1 to 9.2.2 with documented validation
- 2026-05-12 — Investigated noisy Grafana memory alerts and tuned the Proxmox memory threshold
- 2026-05-11 — Published the self-hosted observability stack overview
- 2026-05-11 — Configured Grafana alert rules with Proton SMTP email notifications
- 2026-05-10 — Added Node, Blackbox, and PVE exporters covering Linux VMs, HTTP services, and Proxmox
- 2026-05-09 — Deployed Prometheus and Grafana on a dedicated monitoring VM
- 2026-05-09 — Prepared a reusable Ubuntu Server VM baseline for Docker infrastructure

Full chronology of journal entries, troubleshooting cases, and lab notes: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)

---

## Certification Direction

Certifications are treated as checkpoints along the work, not the work itself. Each one validates real practice rather than driving it.

- **RHCSA** — in progress (RHEL 10 / EX200), the current focus alongside continued Linux administration depth
- **CCNA** — on hold; resumed if a networking-specific path calls for it
- **CKA** — later, only after Kubernetes work is real
- **One cloud certification** — only if it becomes directly relevant to real work

---

## Core Reading Library

Books support the long-term foundation behind this lab. They deepen understanding over time but do not replace real implementation, troubleshooting, or documentation.

### Currently reading

- *Red Hat RHCSA 10 Cert Guide: EX200* — Sander van Vugt
- *CCNA 200-301 Official Cert Guide, Volume 1 & 2*, 2nd Edition — Wendell Odom
- *CCNA 200-301 Hands-on Mastery with Packet Tracer* — Sequeira & Wong
- *Acing the CCNA Exam, Volume 1 & 2* — Jeremy McDowell
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
- **Chose Proxmox VE as the virtualization platform** — open-source, snapshots and backups out of the box, single pane for VMs and storage, and a clear path to clustering — now realized as a two-node HA cluster
- **Chose ZFS replication over Ceph and shared storage** — matched to micro nodes, consumer NVMe without power-loss protection, and a single NIC per node; each node keeps its data local and fast, with no single point of failure
- **Built on capable, modular compute** — Dell Pro Micro Plus nodes (Intel Ultra 7, 64 GB RAM, dual NVMe) — strong enough to host real workloads and modular enough to scale, now running as a two-node HA cluster with a third node planned
- **Standardized on UniFi for the network stack** — consistent management, integrated VLANs and firewall policy, room to grow without changing vendors mid-build
- **Designed VLAN segmentation with seven separate networks** — including a Quarantine VLAN for unknown or untrusted devices, treating segmentation as boundaries of trust, not just address ranges
- **Built secure remote access through WireGuard, Tailscale, and Cloudflare Tunnel** — no open inbound ports beyond a single hardened WireGuard endpoint, with deny-by-default, per-peer access enforced in firewalld
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