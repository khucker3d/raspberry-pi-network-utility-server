# 3. Shared Transfer Drive Setup

<p align="center">
  <img src="https://github.com/khucker3d/infra-raspberry-pi-network-utility-server/blob/main/images/hardware-seagate.JPG" alt="Seagate - One Touch Hub" width="400">
</p>

## Overview

This document describes the sanitized design for a shared transfer drive connected to the Raspberry Pi network utility server. The shared transfer drive provides a local file transfer workflow for trusted devices on the internal network.

## Purpose

The shared transfer drive was created as a temporary internal alternative to cloud-based file transfer workflows. It supports controlled movement of files between trusted systems while helping build practical experience with Linux storage, mounting, permissions, and file-sharing concepts.

## Hardware

* [Seagate - One Touch Hub](https://www.amazon.com/dp/B093X2D4ZM?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_15&th=1)
* 4TB External Hard Drive Desktop HDD
* USB-C and USB 3.0 port

## Design Goals

The setup was designed to:

* Provide local-only file transfer capability
* Avoid unnecessary cloud dependency
* Support trusted internal devices
* Keep storage access simple and documented
* Prepare for future NAS-style workflows
* Practice Linux storage administration
* Maintain public documentation without exposing sensitive details

## High-Level Workflow

```
Trusted Device A
        |
        | Internal Network
        |
Raspberry Pi Utility Server
        |
        | Mounted External Storage
        |
Shared Transfer Drive
        |
        | Internal Network
        |
Trusted Device B
```

## Use Cases

The shared transfer drive supports:

* Moving files between trusted workstations
* Temporary project file staging
* Local backup staging
* Lab file transfer
* Documentation transfer
* Future NAS planning and testing

#### Client Access Testing

The shared transfer drive was validated from multiple trusted client operating systems to confirm that the file-sharing workflow works across platforms.

### macOS Access Test
<img src="https://github.com/khucker3d/infra-raspberry-pi-network-utility-server/blob/main/images/shared-drive-mac.png" alt="macOS Finder showing access to the shared transfer drive" width="500">

### Windows Access Test

<img src="https://github.com/khucker3d/infra-raspberry-pi-network-utility-server/blob/main/images/transfer-shared-pc.png" alt="Windows File Explorer showing access to the shared transfer drive" width="500">

## Storage Concepts Demonstrated

This project demonstrates:

* External drive connection
* Drive identification
* File system validation
* Mount point planning
* Persistent mount configuration
* Permissions planning
* File sharing service configuration
* Client access testing
* Backup considerations

## Security Considerations

The shared transfer drive is designed for trusted internal use only.

Public documentation does not include:

* Share names
* Internal paths
* Usernames
* Passwords
* Device names
* Internal addresses
* Exact permission values
* Private folder structures

## Access Control Principles

The shared transfer workflow should follow these principles:

* Limit access to trusted devices
* Avoid anonymous public access
* Use dedicated accounts where practical
* Keep write access limited
* Separate transfer storage from sensitive long-term storage
* Review files before moving them into permanent storage
* Avoid storing credentials or secrets on the transfer drive

## Future Improvements

Potential future improvements include:

* Dedicated NAS integration
* Separate backup storage
* Automated backup jobs
* Read-only archive shares
* Role-based access groups
* Storage monitoring
* File integrity checks
* Disaster recovery testing

## Skills Demonstrated

This project demonstrates practical experience with:

* Linux storage administration
* External drive setup
* File sharing concepts
* Access control planning
* Internal service design
* Local transfer workflows
* NAS-readiness planning
* Secure public documentation
