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


# Problem 2. Two Router RIP Serial Setup


# Router0

```bash id="hj0kb2"
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface Serial2/0
ip address 10.10.10.1 255.255.255.252
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

```bash id="8qhjcl"
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

interface Serial2/0
ip address 10.10.10.2 255.255.255.252
no shutdown
exit

router rip
network 192.168.2.0
network 10.0.0.0
exit

end
```

---

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


