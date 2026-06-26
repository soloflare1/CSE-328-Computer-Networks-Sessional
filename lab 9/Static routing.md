1
```text
Router> enable
Router# configure terminal

Router(config)# interface FastEthernet0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown

Router(config-if)# exit

Router(config)# interface FastEthernet1/0
Router(config-if)# ip address 192.168.3.10 255.255.255.0
Router(config-if)# no shutdown

Router(config-if)# exit
Router(config)#
```


| Command                                 | Purpose                                        |
| --------------------------------------- | ---------------------------------------------- |
| `enable`                                | Enters Privileged EXEC mode (`Router#`).       |
| `configure terminal`                    | Enters Global Configuration mode.              |
| `interface FastEthernet0/0`             | Selects interface Fa0/0.                       |
| `ip address 192.168.1.1 255.255.255.0`  | Assigns IP address `192.168.1.1/24` to Fa0/0.  |
| `no shutdown`                           | Enables (turns on) the interface.              |
| `exit`                                  | Returns to the previous configuration mode.    |
| `interface FastEthernet1/0`             | Selects interface Fa1/0.                       |
| `ip address 192.168.3.10 255.255.255.0` | Assigns IP address `192.168.3.10/24` to Fa1/0. |
| `no shutdown`                           | Enables Fa1/0.                                 |

### Status messages shown

```text
%LINK-5-CHANGED: Interface FastEthernet0/0, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0, changed state to up

%LINK-5-CHANGED: Interface FastEthernet1/0, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet1/0, changed state to up
```

These messages indicate that both interfaces are **working correctly** and are now **up**.

### Your network

* **Router Fa0/0:** `192.168.1.1/24` (Default Gateway)
* **PC0:** `192.168.1.10/24`
* **PC1:** `192.168.1.11/24`
* **Default Gateway for both PCs:** `192.168.1.1`



2.



```text
Router> enable
Router# configure terminal

Router(config)# interface FastEthernet0/0
Router(config-if)# ip address 192.168.2.1 255.255.255.0
Router(config-if)# no shutdown

Router(config-if)# exit

Router(config)# interface FastEthernet1/0
Router(config-if)# ip address 192.168.3.11 255.255.255.0
Router(config-if)# no shutdown

Router(config-if)# exit

Router(config)# exit
Router#
```

### Explanation

| Command                                 | Description                            |
| --------------------------------------- | -------------------------------------- |
| `enable`                                | Enters Privileged EXEC mode.           |
| `configure terminal`                    | Enters Global Configuration mode.      |
| `interface FastEthernet0/0`             | Selects interface Fa0/0.               |
| `ip address 192.168.2.1 255.255.255.0`  | Assigns IP `192.168.2.1/24` to Fa0/0.  |
| `no shutdown`                           | Turns on the interface.                |
| `exit`                                  | Returns to Global Configuration mode.  |
| `interface FastEthernet1/0`             | Selects interface Fa1/0.               |
| `ip address 192.168.3.11 255.255.255.0` | Assigns IP `192.168.3.11/24` to Fa1/0. |
| `no shutdown`                           | Turns on Fa1/0.                        |
| `exit`                                  | Returns to the previous mode.          |

### Network Configuration

* **Router1 Fa0/0:** `192.168.2.1/24` (Default Gateway)
* **PC2:** `192.168.2.10/24`
* **PC3:** `192.168.2.11/24`
* **Default Gateway (both PCs):** `192.168.2.1`
* **Router1 Fa1/0:** `192.168.3.11/24`

### Connection Between Routers

two routers are configured like this:

| Router  | Interface | IP Address        |
| ------- | --------- | ----------------- |
| Router2 | Fa1/0     | `192.168.3.10/24` |
| Router1 | Fa1/0     | `192.168.3.11/24` |

T
This part of your configuration looks correct. If you're connecting this router to another router using `192.168.3.10`, you'll also need to configure the other router and add routing if the PCs need to communicate with another network.
