# Vic Modern Hotel Network Design and Implementation

## Project Overview

This project showcases the **network design and implementation** for **Vic Modern Hotel**, which spans three floors. Each floor houses different departments, and the design emphasizes secure, scalable, and efficient communication across the entire hotel.

The network setup involves **VLAN segmentation**, **router interconnections**, **OSPF routing**, and **dynamic IP allocation**. Secure remote access via **SSH** and **port security** measures are implemented for added security.

<img src= "https://github.com/ro-drick/Design-and-Implementation-of-a-Hotel-System-Network-Design/blob/main/hotel-network.png">

## Case Study and Requirements

### Hotel Layout and Departmental Distribution

The hotel is structured with various departments spread across three floors:

- **1st Floor**: Reception, Store, and Logistics
- **2nd Floor**: Finance, Human Resources, and Sales/Marketing
- **3rd Floor**: IT and Administration

### Network Design Considerations

- **Router Placement**: Three routers (one per floor) are physically located in the server room within the **IT department** on the 3rd floor.
- **Inter-Router Connectivity**: The routers are interconnected using **serial DCE cables** and configured with the following subnets for communication:
  - 10.10.10.0/30
  - 10.10.10.4/30
  - 10.10.10.8/30
- **VLANs**: Each department is assigned its own VLAN and network address, ensuring proper segmentation and isolation.
- **Wireless Connectivity**: Each floor has wireless access points (Wi-Fi) to connect laptops and smartphones.
- **Printers**: Each department includes a dedicated printer within the VLAN.

### VLAN and Addressing Scheme

The following table outlines the VLANs, department names, and their respective network addresses:

| **Floor**   | **Department** | **VLAN ID** | **Network**          |  
|-------------|----------------|-------------|----------------------|
| **1st Floor**  | Reception      | VLAN 80     | 192.168.8.0/24       |
|               | Store          | VLAN 70     | 192.168.7.0/24       |
|               | Logistics      | VLAN 60     | 192.168.6.0/24       |
| **2nd Floor**  | Finance        | VLAN 50     | 192.168.5.0/24       |
|               | HR             | VLAN 40     | 192.168.4.0/24       |
|               | Sales          | VLAN 30     | 192.168.3.0/24       |
| **3rd Floor**  | Admin          | VLAN 20     | 192.168.2.0/24       |
|               | IT             | VLAN 10     | 192.168.1.0/24       |

### Router Interconnection

The routers on each floor are interconnected using point-to-point links with the following IP addressing scheme:

| **Link**                      | **Network**          |
|-------------------------------|----------------------|
| F2-Router ↔ F3-Router          | 10.10.10.0/30        |
| F2-Router ↔ F1-Router          | 10.10.10.4/30        |
| F1-Router ↔ F3-Router          | 10.10.10.8/30        |

### Key Configurations and Requirements

1. **OSPF Routing**: The network uses **OSPF (Open Shortest Path First)** as the dynamic routing protocol to ensure all routes are advertised between VLANs.
2. **DHCP Server**: Each router on every floor is configured as a **DHCP server** to assign IP addresses dynamically to the devices on the respective floor.
3. **SSH Configuration**: **SSH** is configured on all routers to allow secure remote access for network management.
4. **Port Security**: In the **IT department**, port security is enforced on the switch port **Fa0/1**. The **Test-PC** connected to this port is the only allowed device, and any unauthorized device connection will trigger a **shutdown violation**.

### Addressing Scheme Summary

The network design employs efficient IP addressing for the subnets across different floors. Below is a summary of the IP address allocations:

| **Floor**   | **Network Address** | **VLAN**    | **Subnet Mask** |  
|-------------|---------------------|-------------|-----------------|
| **1st Floor** | 192.168.8.0         | VLAN 80     | 255.255.255.0   |
|               | 192.168.7.0         | VLAN 70     | 255.255.255.0   |
|               | 192.168.6.0         | VLAN 60     | 255.255.255.0   |
| **2nd Floor** | 192.168.5.0         | VLAN 50     | 255.255.255.0   |
|               | 192.168.4.0         | VLAN 40     | 255.255.255.0   |
|               | 192.168.3.0         | VLAN 30     | 255.255.255.0   |
| **3rd Floor** | 192.168.2.0         | VLAN 20     | 255.255.255.0   |
|               | 192.168.1.0         | VLAN 10     | 255.255.255.0   |

## Technologies Utilized

1. **Cisco Packet Tracer**: Used to simulate and implement the network.
2. **Hierarchical Network Design**: Ensures scalability, reliability, and proper network segmentation.
3. **Cabling**: Proper cabling (both wired and wireless) used for the network infrastructure.
4. **VLAN Segmentation**: VLANs created to segment departments based on floor and function.
5. **Subnetting and IP Addressing**: Addressing scheme and subnetting configured for all departments.
6. **Router-on-a-Stick**: Inter-VLAN routing implemented through this method.
7. **DHCP Configuration**: Routers on each floor serve as the DHCP server for dynamic IP addressing.
8. **Secure Remote Access**: **SSH** configured for secure management of routers.
9. **Port Security**: Configured to restrict unauthorized access to critical IT infrastructure.
10. **Wireless Network Setup**: Access points set up to enable wireless connectivity for laptops and mobile devices.

## Testing and Verification

- **Connectivity**: Devices across VLANs and floors were tested to ensure successful communication.
- **DHCP Functionality**: Dynamic IP assignment was tested and confirmed for all devices.
- **Routing**: OSPF routing tables were verified to confirm that routes were properly advertised and learned.
- **SSH Access**: Secure access via SSH was tested from **Test-PC** in the IT department.
- **Port Security**: The port security feature on the IT switch was validated to ensure that only **Test-PC** could access **Fa0/1** and any violation resulted in port shutdown.

## Conclusion

This project successfully demonstrates the design and implementation of a scalable and secure network for a multi-floor hotel, with robust VLAN segmentation, dynamic routing, secure remote access, and wireless connectivity.

---
