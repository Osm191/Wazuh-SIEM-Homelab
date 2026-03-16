# Wazuh SIEM Homelab

![Wazuh](https://img.shields.io/badge/Wazuh-4.7.5-blue)
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-orange)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

## 📋 Overview

I built this Wazuh SIEM to learn security monitoring on my ThinkPad x280 - deploying an Ubuntu 24.04 virtual machine. The goal was to create a functional security monitoring environment capable of detecting and alerting on security events such as unauthorised access attempts, file integrity changes, and system anomalies.

Despite hardware constraints (Device 8GB RAM only - couldn't run the agent separately — managed with our machine.) and Ubuntu 24.04 compatibility challenges, the core SIEM functionality was successfully achieved with security events being generated and logged.

## 🏗️ Architecture

The deployment consists of three main Wazuh components running on a single Ubuntu VM:

- **Wazuh Manager** - Core SIEM engine that analyses collected data and triggers alerts
- **Wazuh Indexer** (Elasticsearch) - Stores and indexes security events
- **Wazuh Dashboard** (Kibana) - Provides visualisation and management interface

## 📸 Screenshots

### Installation Phase

| Screenshot | Description |
|------------|-------------|
| ![Wazuh Installer Running](Wazuh%20installer%20starting%20successfullyjipg) | *Figure 1: Wazuh all-in-one installer executing successfully on Ubuntu 24.04* |
| ![Installation Complete](password%20generation.jpg) | *Figure 2: Installation summary with admin credentials* |
| ![Wazuh Manager Status](Wazuh%20Manager%20installed%20and%20runningjipg) | *Figure 3: Wazuh manager service active and running* |

### Elasticsearch Setup

| Screenshot | Description |
|------------|-------------|
| ![Elasticsearch Active](elastic%20search%20active%20setup.jpg) | *Figure 4: Elasticsearch service enabled and running* |
| ![Elasticsearch Verified](Elastic%20search%20verified%20running%20with%20authenticat...) | *Figure 5: Elasticsearch connection verified via curl authentication* |

### Dashboard State

| Screenshot | Description |
|------------|-------------|
| ![Dashboard Post-Install](Wazuh%20dashboard%20post-installation%20showing%20AP...) | *Figure 6: Dashboard post-installation with API/index errors (expected state)* |
| ![Post-Installation Error State](Wazuh%20post%20installation%20state.jpg) | *Figure 7: Dashboard showing internal server error (API connection issue)* |

### Security Event Detection ✅

| Screenshot | Description |
|------------|-------------|
| ![Raw JSON Alerts](Raw%20JSON%20alert%20data%20showing%20Wazuh%20detecting...) | *Figure 8: Raw JSON alert data confirming Wazuh is detecting Apparmor denials* |
| ![Formatted Alert Logs](Formatted%20alert%20logs%20displaying%20real-time%20security...) | *Figure 9: Formatted alert logs showing real-time security events including Apparmor denials and sudo commands* |

## 🔧 Installation Process

The Wazuh stack was installed using the official all-in-one installer:

```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a -i
