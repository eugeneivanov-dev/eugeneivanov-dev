# Home Infrastructure Lab

Personal infrastructure lab focused on networking, Linux systems, virtualization, self-hosted services, observability, resilience, and long-term growth in infrastructure and systems engineering.

This repository documents practical implementation work, technical decisions, lab architecture, troubleshooting cases, and step-by-step infrastructure development through real projects and written engineering notes.

**Website:** [eugeneivanov.dev](https://eugeneivanov.dev)

---

## Overview

This lab is built to support steady growth in infrastructure and systems engineering through hands-on work.

The focus is not on isolated experiments, but on building, documenting, monitoring, troubleshooting, and improving a structured environment over time.

The long-term direction behind this work includes:

- practical infrastructure implementation
- stronger systems thinking
- operational maturity
- resilience and service reliability
- gradual growth toward system-level design and architecture
- observability and alerting

---

## Current Focus

The current work in this lab is centered on:

- networking and VLAN segmentation
- Linux systems administration
- virtualization with Proxmox VE
- Docker Compose-based self-hosted services
- monitoring and observability with Prometheus and Grafana
- technical documentation and validation
- real implementation logs from the lab

---

## Repositories

### Home Infrastructure Lab
Repository documenting the build-out and evolution of a personal infrastructure lab.

Topics include:

- rack layout and infrastructure design
- network hardware and topology
- virtualization platform build-out
- infrastructure documentation
- hardware setup and deployment
- engineering journal entries with implementation logs

Repository: [github.com/eugeneivanov-dev/homelab](https://github.com/eugeneivanov-dev/homelab)

### Networking Labs
Hands-on networking experiments focused on real infrastructure scenarios.

Topics include:

- DNS configuration and troubleshooting
- VLAN networking and segmentation
- VPN setup and secure remote access
- firewall policy logic
- network troubleshooting and validation

Repository: [github.com/eugeneivanov-dev/networking-labs](https://github.com/eugeneivanov-dev/networking-labs)

### Engineering Journal
Public journal documenting infrastructure work, decisions, experiments, and step-by-step implementation logs from the lab.

- Website: [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)
- GitHub: [github.com/eugeneivanov-dev/homelab/tree/main/journal](https://github.com/eugeneivanov-dev/homelab/tree/main/journal)

---

## Infrastructure Stack

Current infrastructure in the lab includes:

### Physical Infrastructure

- Ubiquiti UniFi Dream Machine Pro Max
- UniFi Pro Max 24 PoE switch
- UniFi Enterprise 8 PoE switch
- 2 × UniFi Lite 8 PoE switches
- 2 × UniFi U7 Pro access points
- Synology RS1221+ NAS
- APC SMT1500RM2UC rackmount UPS
- Dell Pro Micro Plus compute node
- 12U wall-mounted rack
- structured Ethernet cabling and patch panel

### Virtualization and Systems

- Proxmox VE virtualization platform
- Ubuntu Server Linux VMs
- dedicated VMs for separated infrastructure services
- macOS and Windows administrative environments

### Network and Access

- UniFi-based managed network infrastructure
- VLAN segmentation across Main, IoT, Guest, and Lab networks
- firewall rules for network isolation and inter-VLAN traffic control
- Tailscale VPN for secure remote access
- Cloudflare Tunnel for selected self-hosted services

### Self-Hosted Services and Observability

- Docker Compose-based service deployment
- self-hosted analytics platforms: Umami, Plausible, and Matomo
- Prometheus metrics collection
- Grafana dashboards and alert rules
- Node Exporter for Linux VM metrics
- Blackbox Exporter for HTTP service availability checks
- Prometheus PVE Exporter for Proxmox infrastructure metrics
- SMTP-based email alert notifications

Infrastructure documentation: [eugeneivanov.dev/infra](https://eugeneivanov.dev/infra)

---

## Architecture

### Current Architecture

- single-node Proxmox compute foundation
- UniFi-based managed network infrastructure
- VLAN segmentation across the environment
- centralized NAS storage in the lab
- rack-mounted power protection
- dedicated Linux VMs for separated services
- Docker Compose-based deployment model for self-hosted services
- secure remote access through Tailscale VPN and Cloudflare Tunnel
- monitoring and alerting layer for Linux VMs, HTTP services, and Proxmox infrastructure
- documented operational workflows and troubleshooting notes

### Planned Evolution

- broader multi-VM service environment
- more repeatable operational workflows
- deeper NAS integration into infrastructure design
- expansion from 1 Proxmox node to 3 nodes
- more resilient clustered infrastructure
- improved backup, restore, and validation procedures
- stronger system-level analysis and architecture documentation
- Kubernetes only after clustering and resilience foundations are mature

---

## Roadmap

This repository supports a phased infrastructure engineering roadmap focused on practical growth over time.

Current roadmap structure:

1. Networking Foundations
2. Linux, Virtualization, and Core Infrastructure Systems
3. Infrastructure Services and Observability
4. Infrastructure Automation and Operational Maturity
5. Resilient Infrastructure, Clustering, and Kubernetes
6. Systems Architecture and Complex Environment Design

The roadmap is intended to evolve as the lab grows and as deeper technical and architectural understanding develops.

Roadmap: [eugeneivanov.dev/roadmap](https://eugeneivanov.dev/roadmap)

---

## Current Status

### Completed Foundation Work

- structured rack-based infrastructure layout
- UniFi-based managed network stack deployment
- network topology, VLAN segmentation, and isolation
- Proxmox deployed as the first virtualization node
- initial VM-based infrastructure structure established
- Ubuntu Server VMs deployed for separated lab services
- Docker Compose-based self-hosted services deployed
- initial monitoring and alerting stack implemented

### Current Phase

**Infrastructure Services and Observability**

Current and near-term work includes:

- operating and comparing self-hosted analytics services
- expanding monitoring coverage across Linux VMs, HTTP services, and Proxmox
- refining Grafana dashboards and alert rules
- validating failure detection, alert delivery, and recovery behavior
- improving secure remote access patterns
- strengthening service documentation and operational visibility
- continuing Linux administration depth
- preparing for more repeatable operational workflows

---

## Engineering Log

> Recent infrastructure milestones:

- 2026-03-29 — Deployed Proxmox as the first virtualization node in the lab
- 2026-03-30 — Built and documented the initial VM-based infrastructure structure
- 2026-04-03 — Deployed `umami-vm` for self-hosted analytics
- 2026-04-06 — Deployed `minecraft-vm` as an isolated service workload
- 2026-04-10 — Updated the roadmap to reflect a clearer long-term infrastructure direction
- 2026-04-11 — Added certification planning and a core technical reading path to the roadmap
- 2026-05-06 — Updated the Umami analytics stack and validated real tracking data after migration
- 2026-05-07 — Deployed Plausible Analytics as a second self-hosted analytics platform
- 2026-05-07 — Deployed Matomo Analytics using Docker Compose and Cloudflare Tunnel
- 2026-05-09 — Prepared a reusable Ubuntu Server VM baseline for Docker-based infrastructure services
- 2026-05-09 — Deployed Prometheus and Grafana as the core monitoring stack
- 2026-05-10 — Added Node Exporter monitoring for multiple Linux VMs
- 2026-05-10 — Added Blackbox Exporter for HTTP service availability checks
- 2026-05-10 — Added Prometheus PVE Exporter for Proxmox node, VM, and storage metrics
- 2026-05-11 — Organized Grafana dashboards for Linux VMs, HTTP services, and Proxmox infrastructure
- 2026-05-11 — Configured Grafana alert rules and SMTP email notifications
- 2026-05-11 — Published a high-level overview of the self-hosted observability stack
- 2026-05-12 — Investigated a Grafana memory alert and tuned the Proxmox memory alert threshold

---

## Certification Direction

Certifications are treated here as supporting checkpoints for structured learning and gap identification, not as the center of the lab.

Current certification direction:

- CCNA
- RHCSA or LFCS
- CKA later, after clustering and Kubernetes work
- one cloud certification only if it becomes directly relevant to real work

---

## Core Reading Library

Books are part of the long-term learning foundation behind this lab.

Current reading path:

1. *Computer Networking: A Top-Down Approach*  
2. *UNIX and Linux System Administration Handbook*  
3. *The Practice of System and Network Administration*  
4. *Site Reliability Engineering*  
5. *The Site Reliability Workbook*  
6. *Building Secure and Reliable Systems*  
7. *Designing Data-Intensive Applications*  
8. *TCP/IP Illustrated, Volume 1*  

These books support deeper systems understanding over time, but they do not replace real implementation, troubleshooting, documentation, or system design work.

---

## Philosophy

The best way to understand infrastructure is by building, testing, documenting, and improving real systems.

This lab is designed to make technical growth visible through implementation, troubleshooting, structure, and written engineering documentation.

The goal is not only to make systems work, but to understand how they are organized, how they behave, how they fail, and how they can be improved over time.

---

## Key Decisions

- prioritized scalable physical infrastructure from the beginning
- selected modular compute as a foundation for future expansion
- focused on real infrastructure patterns over purely theoretical setups
- treated documentation as part of engineering work, not as an afterthought
- used the lab as a long-term environment for practical infrastructure growth

---

## Links

- **Website:** [eugeneivanov.dev](https://eugeneivanov.dev)
- **Infrastructure:** [eugeneivanov.dev/infra](https://eugeneivanov.dev/infra)
- **Roadmap:** [eugeneivanov.dev/roadmap](https://eugeneivanov.dev/roadmap)
- **Journal:** [eugeneivanov.dev/journal](https://eugeneivanov.dev/journal)
- **LinkedIn:** [linkedin.com/in/eugeneivanov-dev](https://www.linkedin.com/in/eugeneivanov-dev)
- **Home Lab Repository:** [github.com/eugeneivanov-dev/homelab](https://github.com/eugeneivanov-dev/homelab)
- **Networking Labs Repository:** [github.com/eugeneivanov-dev/networking-labs](https://github.com/eugeneivanov-dev/networking-labs)