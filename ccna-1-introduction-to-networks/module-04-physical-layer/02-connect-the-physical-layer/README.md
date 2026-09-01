# Lab 02 — Connect the Physical Layer

<img width="1439" height="899" alt="image" src="https://github.com/user-attachments/assets/0b0db7d4-d83e-4ee7-9228-1f4c98fb9a39" />

## Overview

This Packet Tracer lab focused on identifying the physical characteristics of Cisco networking devices, selecting the appropriate modules, connecting devices using different types of physical media, and verifying connectivity.

The activity reinforced Physical Layer concepts by requiring the identification of management ports, LAN and WAN interfaces, expansion slots, interface bandwidth, cable types, and physical interface status.

---

## Objectives

* Identify the physical characteristics of internetworking devices
* Identify management, LAN, and WAN interfaces
* Determine the default bandwidth of different interfaces
* Identify available expansion slots
* Select the appropriate modules for network connectivity
* Install modules in Cisco networking devices
* Connect devices using the appropriate cable types
* Verify interface status and network connectivity
* Compare wireless and cellular connectivity

---

## Lab Environment

### Devices

* East Router
* West Router
* Switch1
* Switch2
* Switch3
* Switch4
* Access Point
* PC1–PC9
* Laptop
* TabletPC

### Network Technologies

* Ethernet
* Fiber-optic Ethernet
* Serial WAN
* Wireless LAN (WLAN)
* 3G/4G cellular connectivity
* TCP/IP

---

# Part 1 — Identify Physical Characteristics of Internetworking Devices

## 1. Management Ports

The East router was inspected in the Physical workspace to identify the available management ports.

### Management Ports

**Answer:** `[Enter your answer here]`

---

## 2. LAN and WAN Interfaces

The available LAN and WAN interfaces on the East router were identified.

### LAN Interfaces

**Answer:** `[Enter your answer here]`

### WAN Interfaces

**Answer:** `[Enter your answer here]`

### Physical Interfaces

The following command was used to display the router's interfaces:

```bash
East> show ip interface brief
```

The `Vlan1` interface is a virtual interface and does not represent a physical port.

**Number of physical interfaces:** `[Enter your answer here]`

---

## 3. Interface Bandwidth

The default bandwidth of the GigabitEthernet interface was checked using:

```bash
East> show interface gigabitethernet 0/0
```

**Default bandwidth:** `[Enter your answer here]`

The serial interface was then checked using:

```bash
East> show interface serial 0/0/0
```

**Default bandwidth:** `[Enter your answer here]`

### Key Concept — Interface Bandwidth

The bandwidth value displayed on a Cisco interface can be used by routing protocols to calculate the best path to a destination.

For serial interfaces, the configured bandwidth value does **not necessarily represent the actual physical bandwidth of the link**. The actual service speed depends on the WAN service provided by the service provider.

---

## 4. Expansion Slots

The East router was inspected to determine the number of available expansion slots.

**East router:** `[Enter number of slots]`

Switch2 was also inspected.

**Switch2:** `[Enter number of slots]`

---

# Part 2 — Select Correct Modules for Connectivity

## 1. Module for Connecting PCs 1–3

The East router needed to provide connectivity for PC1, PC2, and PC3 without using an additional switch.

### Module Selected

**Answer:** `[Enter module name]`

### Number of Hosts Supported

**Answer:** `[Enter number of hosts]`

The selected module provides additional Ethernet interfaces, allowing multiple end devices to connect directly to the router.

---

## 2. Module for Gigabit Optical Connectivity

Switch2 required a module capable of providing a Gigabit optical connection to Switch3.

### Module Selected

**Answer:** `[Enter module name]`

The module provides a fiber-optic interface for high-speed network connectivity.

---

## Module Installation

The appropriate modules were installed in East and Switch2.

Cisco devices in this activity do not support hot-swapping of these modules. Therefore, the devices had to be powered off before installing or removing modules.

After installation, the devices were powered back on.

### Switch2 Module Slot

The following command was used to identify the interface created by the installed module:

```bash
Switch2> show ip interface brief
```

**Module slot:** `[Enter slot]`

---

# Part 3 — Connect Devices

The devices were connected using the cable types specified by the activity.

| Device  | Interface          | Cable Type              | Device       | Interface          |
| ------- | ------------------ | ----------------------- | ------------ | ------------------ |
| East    | GigabitEthernet0/0 | Copper Straight-Through | Switch1      | GigabitEthernet0/1 |
| East    | GigabitEthernet0/1 | Copper Straight-Through | Switch4      | GigabitEthernet0/1 |
| East    | FastEthernet0/1/0  | Copper Straight-Through | PC1          | FastEthernet0      |
| East    | FastEthernet0/1/1  | Copper Straight-Through | PC2          | FastEthernet0      |
| East    | FastEthernet0/1/2  | Copper Straight-Through | PC3          | FastEthernet0      |
| Switch1 | FastEthernet0/1    | Copper Straight-Through | PC4          | FastEthernet0      |
| Switch1 | FastEthernet0/2    | Copper Straight-Through | PC5          | FastEthernet0      |
| Switch1 | FastEthernet0/3    | Copper Straight-Through | PC6          | FastEthernet0      |
| Switch4 | GigabitEthernet0/2 | Copper Crossover        | Switch3      | GigabitEthernet3/1 |
| Switch3 | GigabitEthernet5/1 | Fiber                   | Switch2      | GigabitEthernet5/1 |
| Switch2 | FastEthernet0/1    | Copper Straight-Through | PC7          | FastEthernet0      |
| Switch2 | FastEthernet1/1    | Copper Straight-Through | PC8          | FastEthernet0      |
| Switch2 | FastEthernet2/1    | Copper Straight-Through | PC9          | FastEthernet0      |
| Switch2 | Gigabit3/1         | Copper Straight-Through | Access Point | Port 0             |
| East    | Serial0/0/0        | Serial DCE              | West         | Serial0/0/0        |

> **Note:** The Serial DCE cable was connected to East first, as required by the activity.

---

# Part 4 — Check Connectivity

## 1. Verify Interface Status on East

The following command was used to verify the status of the East router's interfaces:

```bash
East> show ip interface brief
```

The expected output included:

```text
Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0     172.30.1.1     YES manual up                    up
GigabitEthernet0/1     172.31.1.1     YES manual up                    up
Serial0/0/0            10.10.10.1     YES manual up                    up
Serial0/0/1            unassigned      YES unset  down                  down
FastEthernet0/1/0      unassigned      YES unset  up                    up
FastEthernet0/1/1      unassigned      YES unset  up                    up
FastEthernet0/1/2      unassigned      YES unset  up                    up
FastEthernet0/1/3      unassigned      YES unset  up                    down
Vlan1                  172.29.1.1      YES manual up                    up
```

### Analysis

The output shows that the interfaces required for the lab were operational.

The `up/up` state indicates that both the physical interface and the associated data-link protocol are operational.

The `down/down` state indicates that the physical interface is not operational.

The `up/down` state indicates that the physical layer is operational, but the data-link protocol is not.

---

# 2. Verify Wireless Connectivity

The Laptop was configured to use its wireless interface.

### Steps

1. Open the Laptop's **Config** tab.
2. Select the **Wireless0** interface.
3. Enable **Port Status**.
4. Wait for the wireless connection to become active.
5. Open the Laptop's **Desktop** tab.
6. Open the **Web Browser**.
7. Navigate to:

```text
www.cisco.srv
```

The Cisco Packet Tracer webpage was successfully displayed.

---

# 3. Verify TabletPC Connectivity

The TabletPC was also configured to use its wireless interface.

After enabling the **Wireless0** interface, connectivity to the web server was verified using the web browser.

The Cisco Packet Tracer webpage was successfully displayed.

---

# 4. Change the TabletPC Access Method

The TabletPC was then configured to use its cellular interface instead of its wireless interface.

### Configuration

The **Wireless0** interface was disabled.

The **3G/4G Cell1** interface was enabled.

After the cellular connection was established, web connectivity was tested again.

The Cisco Packet Tracer webpage was successfully displayed.

> **Note:** The Wireless0 and 3G/4G Cell1 interfaces should not be enabled simultaneously during this activity, as this can cause connectivity issues when accessing network resources.

---

# Key Concepts

## Physical Interfaces

Cisco networking devices provide different physical interfaces for different types of network connections, including Ethernet and serial interfaces.

## Interface Naming

Cisco interface names identify the interface type and its location on the device.

For example:

```text
GigabitEthernet0/0
FastEthernet0/1/0
Serial0/0/0
```

Understanding interface naming is essential when configuring Cisco devices through the CLI.

## Modules

Expansion modules allow networking devices to gain additional interfaces or support different types of connectivity.

## Copper Straight-Through

Traditionally used to connect different types of Ethernet devices, such as a router to a switch or a switch to a PC.

## Copper Crossover

Traditionally used to connect similar Ethernet devices, such as switch-to-switch connections.

Modern devices may support **Auto-MDIX**, which can automatically detect and correct transmit and receive pair assignments.

## Fiber

Fiber-optic cables use light to transmit data and are commonly used for high-speed and longer-distance network connections.

## Serial DCE

A DCE cable is used in serial WAN connections and provides clocking for the serial link.

In a Cisco lab environment, the DCE side is typically configured with a clock rate.

## Interface Status

Cisco interface status can be summarized as:

| Status | Protocol | Meaning                                                          |
| ------ | -------- | ---------------------------------------------------------------- |
| Up     | Up       | Physical and data-link layers are operational                    |
| Down   | Down     | Physical interface is not operational                            |
| Up     | Down     | Physical layer is operational, but the data-link protocol is not |

---

# Result

✅ Physical characteristics of Cisco devices identified

✅ Management, LAN, and WAN interfaces identified

✅ Interface bandwidth values examined

✅ Expansion slots identified

✅ Correct modules selected and installed

✅ Devices connected using the appropriate cable types

✅ Serial DCE connection established

✅ Interface status verified using `show ip interface brief`

✅ Wireless connectivity verified

✅ Cellular connectivity verified

✅ End-to-end network connectivity successfully tested

✅ Lab completed successfully
