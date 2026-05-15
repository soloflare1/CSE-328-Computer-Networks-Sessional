Two LAN Connection Using Router (PC0 & PC1)

---

# Problem Statement

Design a network using one router and two PCs (PC0 and PC1).
Each PC is in a different LAN (different network). Configure IP addressing so that both PCs can communicate through the router.

---

# Network Overview

This is a **two LAN connected using one router** setup.

* LAN 1: 192.168.10.0/24
* LAN 2: 192.168.11.0/24

The router connects both LANs and allows communication between them.

---

# IP Addressing Plan

## Router

* FastEthernet0/0 → 192.168.10.1 /24
* FastEthernet1/0 → 192.168.11.1 /24

## PC0 (LAN 10)

* IP Address: 192.168.10.2
* Subnet Mask: 255.255.255.0
* Default Gateway: 192.168.10.1

## PC1 (LAN 11)

* IP Address: 192.168.11.2
* Subnet Mask: 255.255.255.0
* Default Gateway: 192.168.11.1

---

# Router Configuration

```bash id="routereng"
Router>enable
Router#configure terminal

interface fastethernet0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface fastethernet1/0
ip address 192.168.11.1 255.255.255.0
no shutdown
exit

end
```

---

# 6. Cable Type

* Use Copper Cross-Over
* PC to Router connection

---

# 7. Steps

1. Place router and two PCs in Packet Tracer
2. Connect PC0 to FastEthernet0/0
3. Connect PC1 to FastEthernet1/0
4. Configure router interfaces
5. Set IP address, subnet mask, and gateway on PCs
6. Ensure all interfaces are up/up

---

# 8. Testing

From PC0:

```text id="testeng1"
ping 192.168.11.2
```

From PC1:

```text id="testeng2"
ping 192.168.10.2
```

---

# Expected Result

* Successful ping between PC0 and PC1
* Router interfaces show up/up status
* No packet loss in simulation mode

---

# Key Points

* Router connects different networks
* Each LAN must have a different subnet
* Default gateway must be router interface IP
* Correct cable type is required for connectivity
