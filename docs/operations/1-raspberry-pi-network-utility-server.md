# 1. Raspberry Pi Network Utility Server

## Overview

This document describes the sanitized design of a Raspberry Pi-based network utility server used within an enterprise-inspired home infrastructure environment.

The system provides lightweight internal services that support monitoring, DNS visibility, secure administration, file transfer workflows, and future infrastructure expansion.

## Hardware

- [Raspberry Pi 5](https://www.amazon.com/dp/B0CRSNCJ6Y?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1)
- 2.4GHz 64-bit quad-core CPU 
- 8GB RAM
- 128GB Micro SD Card


## Purpose

The Raspberry Pi utility server was deployed to centralize small but important infrastructure services that do not require a full server platform.

This approach provides a practical way to learn and apply systems administration, Linux operations, service management, backup planning, and secure remote access practices.

## Core Functions

The utility server supports the following functions:

* Internal DNS filtering
* Infrastructure uptime monitoring
* Lightweight host metrics
* Secure SSH administration
* Shared transfer drive support
* Service backup and recovery workflows
* Network availability monitoring
* Host-level system health monitoring
* DNS visibility and query monitoring
* Internal service status dashboards

#### Utility Service Examples

The Raspberry Pi utility server hosts several internal-only services, including DNS filtering, uptime monitoring, and host metrics.

![Pi-hole dashboard showing DNS filtering and query visibility](https://github.com/khucker3d/raspberry-pi-network-utility-server/blob/main/images/Pi-hole.png)

![Uptime Kuma dashboard showing monitored infrastructure services](https://github.com/khucker3d/raspberry-pi-network-utility-server/blob/main/images/KumaUpDashboard.png)

![Netdata dashboard showing utility server health metrics](https://github.com/khucker3d/raspberry-pi-network-utility-server/blob/main/images/NetData.png)

## Design Principles

The system was designed using the following principles:

* Internal-only access
* Least privilege administration
* No public WAN exposure
* Documented recovery procedures
* Service separation where practical
* Sanitized public documentation
* Operational simplicity

## High-Level Architecture

```
Trusted Admin Device
        |
        | Secure SSH Access
        |
Raspberry Pi Utility Server
        |
        | Local Services
        |
+-----------------------------+
| DNS Filtering               |
| Uptime Monitoring           |
| System Metrics              |
| Shared Transfer Storage     |
| Backup Support              |
+-----------------------------+
        |
        | Internal Network Only
        |
Enterprise-Inspired Home Network
```

## Service Categories

### DNS and Network Visibility

The utility server provides internal DNS filtering and visibility into local DNS activity. This helps demonstrate how DNS can be used as both a network service and a security control.

### Monitoring

The system supports lightweight monitoring workflows for network infrastructure, internal services, and host-level health checks.

### Network Monitoring

The utility server supports internal monitoring workflows that track network device availability, service reachability, DNS health, and host-level system metrics. This provides operational visibility into the environment while keeping monitoring dashboards internal-only.

### Secure Administration

Administration is performed through SSH from trusted devices only. Public documentation does not include usernames, keys, IP addresses, or administrative paths.

### Shared Transfer Drive

An attached external drive is used for controlled file transfer workflows between trusted systems. This provides a temporary local alternative to cloud-based transfer methods while supporting future NAS planning.

### Backup and Recovery

Utility service configuration and data are backed up using documented procedures. Public documentation describes the recovery strategy without exposing sensitive backup locations or operational details.

## Security Controls

The following controls are applied conceptually:

* Internal-only service exposure
* SSH access limited to trusted administration devices
* No WAN port forwarding
* No public administrative dashboards
* Sensitive values removed from public documentation
* Backup procedures documented separately from private credentials
* External storage used only for trusted internal workflows

## Skills Demonstrated

This project demonstrates practical experience with:

* Linux systems administration
* Raspberry Pi server deployment
* SSH administration
* DNS service planning
* Infrastructure monitoring
* External storage workflows
* Backup and recovery planning
* Secure documentation practices
* Operational runbook development

## Sanitization Notice

This document is intentionally sanitized for public release. Live configuration details, internal addresses, administrative usernames, hostnames, and security-sensitive values have been removed or generalized.

