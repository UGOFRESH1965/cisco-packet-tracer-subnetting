# cisco-packet-tracer-subnetting
A Cisco Packet Tracer lab implementation featuring a /27 IPv4 subnet configuration, router gateway setup, and host-to-host ICMP connectivity verification.

# Cisco Packet Tracer: /27 Subnetting & Basic Topology Implementation

A practical implementation of IPv4 subnetting and basic LAN topology design using Cisco Packet Tracer. This project demonstrates static IP addressing, gateway interface configuration, and end-to-end network connectivity verification across a `/27` network block.

---

## 📐 Network Topology & Requirements

The network consists of a single router serving as the default gateway, connected to a 24-port switch that distributes connectivity across three local host endpoints.

* **Router:** Cisco ISR 4331
* **Switch:** Cisco Catalyst 2960-24TT
* **Endpoints:** 3 PCs (`PC1`, `PC2`, `PC3`)
* **Medium:** Copper Straight-Through Cables

---

## 🧮 Subnetting Scheme

* **Base Network Address:** `192.168.1.0/27`
* **Subnet Mask:** `255.255.255.224`
* **Usable Host Range:** `192.168.1.1` – `192.168.1.30`
* **Broadcast Address:** `192.168.1.31`

### Addressing Table

| Device | Interface | IP Address | Subnet Mask | Default Gateway | DNS Server |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Router0** | `GigabitEthernet0/0/0` | `192.168.1.1` | `255.255.255.224` | N/A | N/A |
| **PC1** | `FastEthernet0` | `192.168.1.10` | `255.255.255.224` | `192.168.1.1` | `192.168.1.2` |
| **PC2** | `FastEthernet0` | `192.168.1.11` | `255.255.255.224` | `192.168.1.1` | `192.168.1.2` |
| **PC3** | `FastEthernet0` | `192.168.1.12` | `255.255.255.224` | `192.168.1.1` | `192.168.1.2` |

---

## ⚙️ Router CLI Configuration

```text
Router> enable
Router# configure terminal
Router(config)# interface GigabitEthernet0/0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.224
Router(config-if)# no shutdown
Router(config-if)# end
Router# copy running-config startup-config
