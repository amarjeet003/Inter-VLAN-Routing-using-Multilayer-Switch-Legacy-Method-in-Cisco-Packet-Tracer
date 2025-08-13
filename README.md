# Inter-VLAN Routing using Multilayer Switch & Legacy Method in Cisco Packet Tracer

## 📌 Overview
This project demonstrates **Inter-VLAN Routing** using both the **Legacy Router-on-a-Stick method** and a **Multilayer Switch** in Cisco Packet Tracer. The setup allows devices in different VLANs to communicate with each other through proper VLAN configuration, trunking, and gateway assignment.

---

## 🖥️ Network Topology
- **VLAN 10**: 192.168.1.0/29  
- **VLAN 20**: 192.168.1.8/29  
- **Subnet Mask**: 255.255.255.248  
- **Gateways**:  
  - VLAN 10 → 192.168.1.6  
  - VLAN 20 → 192.168.1.14  

---

## ⚙️ Configuration Steps

### **Switch 0**
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# exit
Switch(config)# interface range fa0/1-2
Switch(config-if-range)# switchport access vlan 10
Switch(config-if-range)# exit
Switch(config)# interface range fa0/3-4
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit
Switch(config)# interface fa0/5
Switch(config-if)# switchport mode trunk
Switch(config)# interface fa0/6
Switch(config-if)# switchport mode trunk

Switch 1

Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# exit
Switch(config)# interface range fa0/1-2
Switch(config-if-range)# switchport access vlan 10
Switch(config-if-range)# exit
Switch(config)# interface range fa0/3-4
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit
Switch(config)# interface fa0/5
Switch(config-if)# switchport mode trunk


Router-on-a-Stick (Legacy)
Router> enable
Router# configure terminal
Router(config)# interface gigabitEthernet 0/0
Router(config-if)# no shutdown
Router(config)# interface gigabitEthernet 0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.1.6 255.255.255.248
Router(config)# interface gigabitEthernet 0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.1.14 255.255.255.248

Multilayer Switch Method
bash
Copy
Edit
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# exit
Switch(config)# interface vlan 10
Switch(config-if)# ip address 192.168.1.6 255.255.255.248
Switch(config-if)# exit
Switch(config)# interface vlan 20
Switch(config-if)# ip address 192.168.1.14 255.255.255.248
Switch(config-if)# exit
Switch(config)# ip routing

📊 Testing
Ping between VLANs to verify inter-VLAN communication.
Check connectivity using ping <IP> from different PCs.
Observe packet flow in Simulation Mode in Cisco Packet Tracer.

## Outcome
- Implemented Inter-VLAN Routing using both Router-on-a-Stick and Multilayer Switch methods.
- Achieved successful communication between devices in different VLANs.
- Configured VLANs, trunk ports, and gateways for proper routing.
- Verified connectivity with ping tests showing 0% packet loss after setup.
