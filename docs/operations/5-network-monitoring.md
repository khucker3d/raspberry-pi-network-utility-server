# 5. Network Monitoring

## Overview

This document describes the sanitized network monitoring approach used within the enterprise-inspired home infrastructure project.

The monitoring setup provides visibility into network availability, utility services, and host health while keeping all dashboards and administrative interfaces internal-only.

## Purpose

The goal of the monitoring design is to detect service outages, infrastructure failures, and host-level issues before they become larger operational problems.

This setup also demonstrates practical experience with infrastructure monitoring, service validation, operational documentation, and incident response readiness.

## Monitoring Scope

The monitoring system tracks the availability and health of key internal infrastructure components, including:

* Network gateway
* Network controller
* Wireless access point
* Network switch
* DNS filtering service
* Utility server
* Monitoring services
* Security lab dashboards
* Shared infrastructure services

## Monitoring Services

The monitoring design uses multiple layers of visibility. Uptime monitoring is used to verify whether important network devices and internal services are reachable. This provides a quick operational view of service availability and helps identify outages affecting core infrastructure.

Example monitored categories include:

* Gateway availability
* Controller availability
* Wireless infrastructure availability
* DNS service availability
* Internal dashboard availability
* Utility server availability

#### Monitoring Dashboard Example
The monitoring dashboard provides a centralized view of internal service availability, including network devices, DNS services, infrastructure dashboards, and lab systems.

![UpTime Kuma](https://github.com/khucker3d/raspberry-pi-network-utility-server-public/blob/main/images/KumaUpDashboard.png)

### Host Health Monitoring

Host-level monitoring is used to observe the health of the utility server.

Example metrics include:

* CPU usage
* Memory usage
* Disk usage
* Network traffic
* System load
* Temperature
* Container or service status

#### Host Metrics Example

Host-level metrics are used to monitor the utility server’s CPU, memory, disk, network, and system health.

![Netdata dashboard showing utility server host metrics](https://github.com/khucker3d/raspberry-pi-network-utility-server-public/blob/main/images/NetData.png)

### DNS Visibility

DNS monitoring provides visibility into internal name resolution activity and blocked queries.

This supports both operational troubleshooting and basic security awareness by showing whether clients are using the expected DNS path.

### Security Monitoring

Security monitoring is handled separately from basic uptime monitoring.

Security-focused tools are used to collect and analyze security-relevant events from lab systems and monitored endpoints.

#### Security Monitoring Example

Security monitoring is handled separately from basic uptime monitoring. A security dashboard is used in the lab environment to review endpoint, file integrity, threat hunting, and vulnerability-related data.

![Wazuh dashboard showing security monitoring categories](https://github.com/khucker3d/raspberry-pi-network-utility-server-public/blob/main/images/WazuhDashboard.png)

## High-Level Monitoring Architecture

```
Internal Network Devices
        |
        | Availability Checks
        |
Uptime Monitoring Service
        |
        | Status Dashboard
        |
Trusted Admin Device


Utility Server
        |
        | Host Metrics
        |
System Health Monitoring
        |
        | Resource Visibility
        |
Trusted Admin Device


Internal Clients
        |
        | DNS Queries
        |
DNS Filtering Service
        |
        | Query Visibility
        |
Trusted Admin Device
```

## Alerting Strategy

The alerting strategy prioritizes critical infrastructure failures.

Potential alert categories include:

* Gateway unreachable
* DNS service unavailable
* Utility server unavailable
* Monitoring dashboard unavailable
* Wireless infrastructure unavailable
* Storage or disk usage issue
* High system resource usage
* Temperature or hardware health concern

Alerts should be tuned to reduce noise and focus on events that require action.

#### Alerting Example

Alert notifications are used to validate that service outages and recoveries are detected and reported through the expected notification channel.

![Discord alert test showing service down and recovery notifications](https://github.com/khucker3d/raspberry-pi-network-utility-server-public/blob/main/images/DiscordNotification.png)

## Operational Workflow

When an alert or outage occurs, the basic workflow is:

1. Confirm whether the affected device or service is reachable
2. Check whether the issue affects one service or multiple services
3. Review utility server health metrics
4. Confirm DNS resolution if client connectivity is affected
5. Check physical connectivity if a network device is unreachable
6. Review recent configuration changes
7. Restore service or roll back the last known change if needed
8. Document the incident and resolution

## Security Considerations

The monitoring environment is designed for internal use only.

Public documentation intentionally omits:

* Internal IP addresses
* Hostnames
* Monitor names
* Dashboard URLs
* Alert webhook URLs
* API tokens
* Notification endpoints
* Service credentials
* Client names
* DNS query details

## Public Documentation Approach

The public version focuses on architecture and operational practice rather than live implementation details.

Screenshots should be avoided or heavily sanitized before publication. Diagrams should use generic labels instead of real network values.

## Skills Demonstrated

This monitoring setup demonstrates practical experience with:

* Network availability monitoring
* Service health checks
* Linux host monitoring
* DNS visibility
* Infrastructure troubleshooting
* Alert planning
* Incident response workflow design
* Internal-only dashboard security
* Secure public documentation practices
