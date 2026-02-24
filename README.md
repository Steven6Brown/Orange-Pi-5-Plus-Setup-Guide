# Orange Pi 5 Plus Setup & Configuration Guide

A complete hardware and software setup guide for configuring an Orange Pi 5 Plus as a network monitoring node. Written during an internship at Digital Cloak, this guide covers everything from physical assembly to deploying Kismet for wireless device capture and Metricbeat for system monitoring.

## Overview

The Orange Pi 5 Plus was configured to function as a lightweight, deployable network monitoring node — designed to work alongside geo pucks and Kismet to passively capture and track wireless device activity on networks. Once set up, the device ships system metrics back to a centralized ELK Stack for real-time monitoring and analysis.

## What This Guide Covers

- **Hardware Assembly** — Installing the eMMC module, heat sinks, NVMe SSD, and WiFi card
- **OS Installation** — Flashing Armbian onto the eMMC and initial system configuration
- **Kismet Setup** — Configuring Kismet for both WiFi (ALFA card) and RTL-SDR capture
- **Metricbeat Integration** — Installing and configuring Metricbeat to ship metrics to an ELK Stack
- **System Testing** — Verifying each component is functioning correctly at each stage

## Hardware Used

| Component | Description |
|---|---|
| Orange Pi 5 Plus (32GB) | Primary single-board computer |
| Orange Pi eMMC Module (256GB) | Primary storage |
| Samsung 990 EVO NVMe SSD (2TB) | Secondary storage |
| Orange Pi WiFi Card (R6) | Internal WiFi |
| ALFA WiFi Card | External WiFi card for Kismet capture |
| Nooelec RTL-SDR | Software-defined radio for RTL-SDR capture |
| GlobalSat GeoPuck | USB GPS receiver |
| RevoData PoE Splitter | Power over Ethernet |
| 52pi Metal Case & Heat Sinks | Cooling and enclosure |

## Software Used

| Software | Purpose |
|---|---|
| Armbian (Desktop) | Operating system |
| Kismet | Wireless network monitoring and device capture |
| Metricbeat | Ships system metrics to ELK Stack |
| ELK Stack | Centralized logging and real-time data visualization |

## Getting Started

Refer to the full setup guide for step-by-step instructions:

1. [Required Tools](Orange%20Pi%205%20Plus%20Setup%20%26%20Configuration%20Guide.md#required-tools)
2. [Assembly](Orange%20Pi%205%20Plus%20Setup%20%26%20Configuration%20Guide.md#assembly)
3. [Startup](Orange%20Pi%205%20Plus%20Setup%20%26%20Configuration%20Guide.md#startup)
4. [Kismet Configuration](Orange%20Pi%205%20Plus%20Setup%20%26%20Configuration%20Guide.md#kismet)
5. [Metricbeat Configuration](Orange%20Pi%205%20Plus%20Setup%20%26%20Configuration%20Guide.md#metricbeat)

## Notes

- This guide was written for the Orange Pi 5 Plus running Armbian. Steps may vary for other operating systems or board versions.
- Metricbeat version should match your ELK Stack version. This guide uses version 8.14.1.
- Static IP addresses should be assigned to each device for reliable tracking within the network.

## Author

**Steven Brown**  
Cybersecurity Analytics and Operations, Penn State University  
[LinkedIn](https://www.linkedin.com/in/stevenrbrown) | [Portfolio](https://stevenrbrown.org)
