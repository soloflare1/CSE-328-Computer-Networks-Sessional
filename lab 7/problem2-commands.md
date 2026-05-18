
# Router Configuration

## Router 1

```bash
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface Serial2/0
ip address 10.10.10.1 255.0.0.0
clock rate 64000
no shutdown
exit

router rip
network 192.168.1.0
network 10.0.0.0
exit
````

---

## Router 2

```bash
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

interface Serial2/0
ip address 10.10.10.2 255.0.0.0
no shutdown
exit

router rip
network 192.168.2.0
network 10.0.0.0
exit
```

---

# PC Configuration

## PC1

```text
IP Address : 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
```

## PC2

```text
IP Address : 192.168.2.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.2.1
```

---

# Test Connectivity

## From PC1

```bash
ping 192.168.2.2
```

## From PC2

```bash
ping 192.168.1.2
```


```
```
