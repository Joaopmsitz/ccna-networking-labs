# Lab 05 — Basic Switch and End Device Configuration

<img width="1439" height="899" alt="image" src="https://github.com/user-attachments/assets/1dc57bf8-4ba8-45cd-b598-6f99819633bf" />

## Overview

This Packet Tracer activity consolidated the basic Cisco IOS configuration and IPv4 connectivity skills practiced throughout the previous labs.

The objective was to configure two Cisco switches and two end devices in a small wired LAN, including hostname configuration, password protection, password encryption, MOTD banners, IPv4 addressing, configuration persistence, and connectivity verification.

Unlike the previous guided labs, this activity provided dynamically generated requirements that had to be identified and implemented correctly.

---

## Objectives

* Configure hostnames on two Cisco switches
* Configure console and privileged EXEC security
* Encrypt plaintext passwords
* Configure MOTD banners
* Configure IPv4 addresses on switches and PCs
* Save device configurations
* Verify connectivity between end devices
* Validate the complete LAN configuration

---

## Lab Environment

### Network Devices

* Cisco Switch — S1
* Cisco Switch — S2

### End Devices

* PC1
* PC2

### Network Topology

```text
PC1 ───── S1 ───── S2 ───── PC2
```

---

## Addressing

The activity generated the addressing requirements dynamically.

| Device | Interface | IP Address           | Subnet Mask     |
| ------ | --------- | -------------------- | --------------- |
| S1     | VLAN 1    | Assigned by activity | `255.255.255.0` |
| S2     | VLAN 1    | Assigned by activity | `255.255.255.0` |
| PC1    | NIC       | Assigned by activity | `255.255.255.0` |
| PC2    | NIC       | Assigned by activity | `255.255.255.0` |

> The exact addressing values may change when the Packet Tracer activity is reset.

---

# Configuration Requirements

The activity required the following configuration on both switches:

* Hostname
* Console line password
* Privileged EXEC secret
* Password encryption
* MOTD banner
* Management IP address
* Configuration saved to NVRAM

The PCs were configured with the IPv4 addresses specified by the activity.

---

# Switch Configuration

## Hostname

Each switch was configured with its assigned hostname:

```text
Switch(config)# hostname S1
```

The same process was performed on S2.

---

## Console Security

Console access was protected using the assigned line password:

```text
S1(config)# line console 0
S1(config-line)# password <LinePW>
S1(config-line)# login
```

The `login` command ensures that the configured password is actually requested when accessing the console.

---

## Privileged EXEC Security

The privileged EXEC mode was protected using an encrypted secret:

```text
S1(config)# enable secret <SecretPW>
```

`enable secret` is preferred over `enable password` because the secret is stored in a protected hashed form in the configuration.

---

## Password Encryption

Plaintext passwords were encrypted using:

```text
S1(config)# service password-encryption
```

This provides an additional layer of protection for plaintext passwords stored in the running configuration.

---

## MOTD Banner

A Message of the Day banner was configured to warn unauthorized users:

```text
S1(config)# banner motd "Authorized Access Only!"
```

The same requirement was applied to S2.

---

# IP Configuration

## Switch Management Interfaces

The switches were configured with management IP addresses through VLAN 1.

### S1

```text
S1(config)# interface vlan 1
S1(config-if)# ip address <S1Add> 255.255.255.0
S1(config-if)# no shutdown
```

### S2

```text
S2(config)# interface vlan 1
S2(config-if)# ip address <S2Add> 255.255.255.0
S2(config-if)# no shutdown
```

The SVI provides an IP-based management interface for the switches.

---

## PC Configuration

PC1 and PC2 were configured through the Packet Tracer Desktop → IP Configuration interface.

### PC1

```text
IP Address:  <PC1Add>
Subnet Mask: 255.255.255.0
```

### PC2

```text
IP Address:  <PC2Add>
Subnet Mask: 255.255.255.0
```

Both PCs were configured within the same IPv4 subnet to allow direct communication.

---

# Configuration Verification

The switch configurations were verified using IOS commands such as:

```text
S1# show running-config
```

and:

```text
S1# show ip interface brief
```

These commands were used to verify:

* Hostname
* Console configuration
* Password security
* MOTD banner
* Management IP address
* Interface status

The same verification process was performed on S2.

---

# Saving the Configuration

The completed configurations were saved to NVRAM:

```text
S1# copy running-config startup-config
S2# copy running-config startup-config
```

Saving the configuration ensures that the configuration is retained after a device reboot.

---

# Connectivity Verification

After configuring all devices, connectivity was tested using `ping`.

Examples:

```text
PC1> ping <PC2Add>
```

```text
PC1> ping <S1Add>
```

```text
PC1> ping <S2Add>
```

<img width="1439" height="898" alt="image" src="https://github.com/user-attachments/assets/e5a31bda-d2bb-40ed-b79b-8bdc0f244027" />


The objective was to achieve successful connectivity between the devices in the LAN.

Successful ping responses confirmed that:

* The PCs had valid IPv4 configurations.
* The switches had valid management IP addresses.
* The devices were connected correctly.
* The devices were operating within the expected subnet.
* Basic network connectivity was functioning.

---

# Key Commands

| Purpose                       | Command                              |
| ----------------------------- | ------------------------------------ |
| Enter Privileged EXEC         | `enable`                             |
| Enter Global Configuration    | `configure terminal`                 |
| Configure hostname            | `hostname S1`                        |
| Configure console             | `line console 0`                     |
| Configure console password    | `password <LinePW>`                  |
| Enable console authentication | `login`                              |
| Configure privileged secret   | `enable secret <SecretPW>`           |
| Encrypt plaintext passwords   | `service password-encryption`        |
| Configure MOTD                | `banner motd "message"`              |
| Enter management SVI          | `interface vlan 1`                   |
| Configure IP address          | `ip address <ip> <mask>`             |
| Enable SVI                    | `no shutdown`                        |
| Verify interfaces             | `show ip interface brief`            |
| Verify configuration          | `show running-config`                |
| Save configuration            | `copy running-config startup-config` |
| Test connectivity             | `ping <ip>`                          |

---

