# Lab 01 — Connect a Wired and Wireless LAN

<img width="1439" height="899" alt="image" src="https://github.com/user-attachments/assets/108182f9-1ddf-49a2-af60-8eb1acb75ca7" />

## Overview

This Packet Tracer lab focused on connecting a wired and wireless network using the correct cable types and verifying connectivity between devices.

The activity reinforced Physical Layer concepts by requiring the selection of appropriate media, establishing device connections, testing communication, and examining the physical network topology.

---

## Objectives

- Connect devices using the appropriate cable types
- Identify straight-through, crossover, serial, coaxial, and console cables
- Verify network connectivity
- Explore logical and physical topologies
- Analyze communication between wired and wireless networks

---

## Lab Environment

### Devices

- Cloud
- Cable Modem
- Router0
- Router1
- Wireless Router
- Switch
- Configuration Terminal
- Netacad Server
- Family PC
- Home PC
- Home Printer

### Network Technologies

- Ethernet
- WLAN
- Serial WAN
- Coaxial Communication
- TCP/IP

---

# Network Topology

The completed topology included:

```text
Family PC
    │
    └── Wireless Router
            │
            └── Cable Modem
                    │
                  Cloud
                    │
                 Router0
                /       \
      Netacad Server   Router1
                            │
                         Switch
```

The Wireless Router also provided wireless connectivity to:

- Home PC
- Home Printer

---

# Part 1 — Connect to the Cloud

The Cloud was connected to both Router0 and the Cable Modem.

| From | To | Cable Type |
|--------|--------|--------|
| Cloud Eth6 | Router0 F0/0 | Copper Straight-Through |
| Cloud Coax7 | Cable Modem Port0 | Coaxial |

### Key Concept

The cloud represents the service provider network that interconnects enterprise and residential networks.

---

# Part 2 — Connect Router0

Router0 was connected to several devices using different media types.

| From | To | Cable Type |
|--------|--------|--------|
| Router0 S0/0/0 | Router1 S0/0 | Serial |
| Router0 F0/1 | Netacad Server F0 | Copper Crossover |
| Router0 Console | Configuration Terminal RS232 | Console |

### Key Concepts

#### Serial Cable

Used for WAN communication between routers.

#### Copper Crossover

Used because the router and server use the same transmit and receive pairs.

#### Console Cable

Provides out-of-band access for device management and configuration.

---

# Part 3 — Connect Remaining Devices

Additional infrastructure and end devices were connected.

| From | To | Cable Type |
|--------|--------|--------|
| Router1 F1/0 | Switch F0/1 | Copper Straight-Through |
| Cable Modem Port1 | Wireless Router Internet | Copper Straight-Through |
| Wireless Router Eth1 | Family PC F0 | Copper Straight-Through |

Wireless connectivity was provided to:

- Home PC
- Home Printer

---

# Part 4 — Connectivity Verification

Connectivity was tested from the Family PC.

### Ping Test

```bash
ping netacad.pka
```

Result:

```text
Pinging 10.0.0.254 with 32 bytes of data:

Reply from 10.0.0.254: bytes=32 time=2ms TTL=126
Reply from 10.0.0.254: bytes=32 time=9ms TTL=126
Reply from 10.0.0.254: bytes=32 time=28ms TTL=126
Reply from 10.0.0.254: bytes=32 time=59ms TTL=126
```

<img width="1439" height="899" alt="image" src="https://github.com/user-attachments/assets/f0c85545-1b18-461a-82bf-bc5e5251b8e2" />

### Analysis

The successful ping confirmed:

- Proper cabling
- End-to-end IP connectivity
- Communication between wired and wireless segments
- Correct device interconnection

---

# Addressing Summary

| Device | Interface | IP Address |
|----------|----------|----------|
| Router0 | F0/0 | 192.168.2.1/24 |
| Router0 | F0/1 | 10.0.0.1/24 |
| Router0 | S0/0/0 | 172.31.0.1/24 |
| Router1 | S0/0 | 172.31.0.2/24 |
| Router1 | F1/0 | 172.16.0.1/24 |
| Wireless Router | Internet | 192.168.2.2/24 |
| Wireless Router | Eth1 | 192.168.1.1 |
| Family PC | F0 | 192.168.1.102 |
| Switch | F0/1 | 172.16.0.2 |
| Netacad Server | F0 | 10.0.0.254 |

---

# Physical Topology Analysis

The Packet Tracer Physical Workspace was explored to examine different networking environments.

### Observations

- Enterprise equipment is commonly installed in racks for organization and scalability.
- Home networks typically use fewer devices and do not require dedicated racks.
- Different cable types serve different networking purposes.
- Physical and logical topologies provide different perspectives of the same network.

---

# Cable Types Used

| Cable Type | Purpose |
|------------|----------|
| Copper Straight-Through | Connect different device types |
| Copper Crossover | Connect similar device types |
| Serial | Router-to-router WAN connection |
| Coaxial | Cloud to Cable Modem connection |
| Console | Device management |

---

## Result

✅ Correct cable types selected

✅ Wired devices successfully connected

✅ Wireless devices successfully connected

✅ WAN serial link established

✅ Connectivity to the Netacad server verified

✅ Physical topology explored

✅ Lab completed successfully

✅ Console access validated

✅ Physical topology explored

✅ Lab completed successfully
