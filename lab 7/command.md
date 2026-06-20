1. **2 Switch + 1 Router setup**
2. **2 Router Serial RIP setup**


# Problem 1. Two Switch + One Router Setup

## IP Configuration

### Switch 1 Network

| PC  | IP Address   |
| --- | ------------ |
| PC0 | 192.168.1.10 |
| PC1 | 192.168.1.11 |
| PC2 | 192.168.1.12 |

Gateway: `192.168.1.1`

---

### Switch 2 Network

| PC  | IP Address   |
| --- | ------------ |
| PC3 | 192.168.2.10 |
| PC4 | 192.168.2.11 |
| PC5 | 192.168.2.12 |

Gateway: `192.168.2.1`

---

# Connection
Switch-2960
Router-1941
* PC → Switch = Straight Through
* Switch → Router = Straight Through
* Router ports:

  * Switch1 → `GigabitEthernet0/0`
  * Switch2 → `GigabitEthernet0/1`

---

# Router Configuration

```bash
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

end
```

---

# Set Default Gateway

## PCs in Switch1

```text
192.168.1.1
```

## PCs in Switch2

```text
192.168.2.1
```

---

# Ping Again

From PC0:

```bash
ping 192.168.2.10
```
---
------------------------------------------------------------------------
# Testing Procedure

After completing the network configuration, step-by-step connectivity tests were performed to verify proper communication.

---

## Step 1: LAN1 Test

First, a ping test was performed from PC0 to the default gateway (Router interface for LAN1):

```
PC0 > ping 192.168.1.1
```

Purpose:
To verify that the LAN1 network and Router interface (G0/0) are working properly.

---

## Step 2: LAN2 Router Test

Next, a ping test was performed from PC3 to the Router interface of LAN2:

```
PC3 > ping 192.168.2.1
```

Purpose:
To ensure that the LAN2 network and Router interface (G0/1) are correctly configured and reachable.

---

## Step 3: Cross-Network Test

Finally, communication between two different networks was tested:

```
PC0 > ping 192.168.2.10
```

Purpose:
To verify inter-network routing between LAN1 and LAN2 through the router.

---

## Final Observation

If Step 1 and Step 2 are successful, it confirms that both router interfaces are working correctly. If Step 3 is successful, it confirms that inter-network routing is properly configured and functioning.
-------------------------------------------------------------------------
# Problem 2. Two Router RIP Serial Setup


# Router0

```bash id="l0gqxr"
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.1.1 255.0.0.0
no shutdown
exit

interface Serial0/1/0
ip address 10.10.10.1 255.0.0.0
no shutdown
exit

router rip
network 192.168.1.0
network 10.0.0.0
exit

end
```

---

# Router1

```bash id="u4tbm5"
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.2.1 255.0.0.0
no shutdown
exit

interface Serial0/1/0
ip address 10.10.10.2 255.0.0.0
no shutdown
exit

router rip
network 192.168.2.0
network 10.0.0.0
exit

end
```

---

# Connection

```text id="3jlgom"

Router-1941

PC0 FastEthernet0 -------- FastEthernet0/0 Router0
Router0 Serial0/1/0 -------- Serial0/1/0 Router1
Router1 FastEthernet0/0 -------- FastEthernet0 PC1
```

* PC ↔ Router = Copper Cross-Over
* Router ↔ Router = Serial DTE


# PC0

```text id="d5m9ee"
IP: 192.168.1.2
Mask: 255.255.255.0
Gateway: 192.168.1.1
```

# PC1

```text id="0i3yvr"
IP: 192.168.2.2
Mask: 255.255.255.0
Gateway: 192.168.2.1
```

---

Test:

```bash id="4wktwa"
ping 192.168.2.2
```


