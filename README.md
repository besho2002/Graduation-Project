# Enterprise Network Infrastructure and Security Project 🌐🛡️

## Overview
This repository contains the comprehensive documentation, configurations, and topology designs for a multi-site enterprise network infrastructure. Developed by an Information Technology Graduate from Assiut Technological University[cite: 14], this project focuses on building a highly available, secure, and monitored architecture, integrating advanced routing, switching, and centralized cybersecurity operations.

## Network Architecture & Geographic Topology 🏗️
The infrastructure is designed with a scalable, multi-site approach, consisting of three distinct branches connected securely:
* **Cairo Headquarters (HQ):** The main operational hub utilizing the `172.16.40.0/24` network block[cite: 14].
* **USA Branch:** A remote enterprise branch utilizing the `172.16.30.0/24` network block, connected via secure Site-to-Site IPsec VPN tunnels[cite: 14].
* **Cloud Branch:** Integrating cloud-based resources to simulate a modern hybrid-cloud enterprise environment.

## IP Addressing & Subnetting Strategy (IPAM) 🧮
* **Major Network Block:** The enterprise utilizes a Class B Private IP Range (`172.16.0.0/16`)[cite: 14].
* **Subnetting Methodology:** A Fixed-Length Subnet Mask (FLSM) with a `/27` prefix (`255.255.255.224`) is implemented within the main branches[cite: 14]. 
* **Scalability:** This strategy divides branches into smaller, secure departmental broadcast domains, providing 30 usable host IP addresses per segment[cite: 14].
* **VLAN Segmentation:** Standardized VLANs across branches include Management (VLAN 10), HR (VLAN 20), IT (VLAN 30), Finance & Accounting (VLAN 40), Sales (VLAN 50), PR (VLAN 60), Customer Service (VLAN 70), and Core Servers (VLAN 80)[cite: 14].

## Dynamic IP Address Management (DHCP Infrastructure) ⚙️
To automate IP allocation and prevent human error, a robust DHCP infrastructure was deployed:
* **Lightweight Deployment:** Centralized DHCP servers were deployed on Alpine Linux to maintain a lightweight footprint within the simulation[cite: 15].
* **Daemon Configuration:** The native Alpine package manager was utilized to install the ISC DHCP server daemon (`dhcp-server-vanilla`)[cite: 15].
* **Traffic Optimization:** Two distinct DHCP servers were deployed for the geographically separated branches to ensure DHCP broadcast traffic remains confined to its respective local area network, optimizing WAN link bandwidth[cite: 15].

## Cybersecurity & Centralized Monitoring (SOC / SIEM) 🛡️📊
### Zabbix Implementation
* **Proactive Monitoring:** Zabbix (Version 7.4.10) was implemented for proactive management and real-time visibility[cite: 18].
* **SNMP Integration:** SNMP is heavily utilized to fetch telemetry data from Cisco routing and switching equipment (e.g., `Cisco_ASA_Core` and `Switch_Servers`)[cite: 18].
* **Incident Detection:** The system successfully detects resource exhaustion, such as High memory utilization (>90% for 5m) on the firewall instance[cite: 18].
* **Telegram Webhook Alerting:** A Telegram Webhook was established to route alerts externally, sending immediate push notifications directly to the Administrator's Telegram account to drastically reduce the Mean Time to Respond (MTTR)[cite: 18].

### SIEM & Security Policies
* **Threat Detection:** Splunk and Wazuh are utilized for centralized log management and threat detection on cloud nodes.
* **Access Control:** Strict firewall policies and ACLs are implemented across Cisco ASA and Fortinet (FortiGate) devices.

## Repository Structure & Download 📂
* [📥 Download Full GNS3 Project - 500MB](https://drive.google.com/drive/folders/1cu1PZuXTsmGit4i3EAwPg-3f7XlGirFZ?usp=sharing) -> Click here to download the complete simulation project environment with all embedded device images.
* `/Topologies`: Contains high-resolution diagrams of the multi-site network.
* `/Configurations`: Backup configuration files for Cisco routers/switches, Cisco ASA, and FortiGate firewalls.
* `/Monitoring_and_Security`: Scripts and configuration snippets for Zabbix, Splunk, Wazuh, and the Telegram webhook integration.
