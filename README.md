# Cafe WiFi Hotspot: Network Segmentation & Security

A Cisco Packet Tracer project demonstrating a secure, multi-department network architecture for a commercial cafe environment. This project focuses on **VLAN segmentation**, **Inter-VLAN routing (Router-on-a-Stick)**, and **Access Control Lists (ACLs)** to ensure guest privacy and internal data security.

## 🚀 Overview

This repository contains the network topology and configuration for a cafe hotspot. The network is divided into five distinct departments to optimize performance and security:

* **VLAN 10 (Staff/Server):** Contains the Cafe Server and Cashier systems.
* **VLAN 20 (Guests):** Wireless access for customers with restricted permissions.
* **VLAN 30 (Management):** For Manager, Accountant, and Admin workstations.
* **VLAN 40 (Kitchen):** Internal communication for kitchen staff.
* **VLAN 50 (CCTV):** Isolated network for security camera monitoring.

## 🛠️ Technical Specifications

### Network Topology
* **Router:** Cisco 2911 (Handling Inter-VLAN routing via sub-interfaces).
* **Switch:** Cisco 2960-24TT (Layer 2 distribution with Trunking).
* **Access Point:** Providing wireless connectivity for Guest laptops and smartphones.

### IP Schema
| Department | VLAN | Subnet | Gateway |
| :--- | :--- | :--- | :--- |
| Staff/Server | 10 | 192.168.10.0/24 | 192.168.10.1 |
| Guests | 20 | 192.168.20.0/24 | 192.168.20.1 |
| Management | 30 | 192.168.30.0/24 | 192.168.30.1 |
| Kitchen | 40 | 192.168.40.0/24 | 192.168.40.1 |
| CCTV | 50 | 192.168.50.0/24 | 192.168.50.1 |

## 🔒 Security Implementation (ACL)

The project implements an **Extended Access Control List** (`GUEST_RESTRICTION`) applied to the Guest VLAN interface. 

**Logic:**
1.  **Permit HTTP:** Guests can access the Cafe Web Server (192.168.10.2).
2.  **Deny Internal Access:** All traffic from Guests to Staff, Management, Kitchen, and CCTV subnets is blocked.
3.  **Permit All Else:** General internet/external traffic is allowed for guest browsing.

## 📂 Project Structure
* `/Topology`: Contains the `.pkt` (Packet Tracer) file.
* `/Configs`: Text files of the Router and Switch CLI configurations.

## 📝 How to Use
1. Download and install **Cisco Packet Tracer**.
2. Clone this repository.
3. Open the `.pkt` file to view the live simulation.
4. Verify connectivity by pinging between departments (Internal) and testing ACL restrictions from a Guest device.
