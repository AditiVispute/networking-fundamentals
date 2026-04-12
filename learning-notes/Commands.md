# Switch Commands (Cisco Switch CLI)

---

## Introduction

A network switch is configured using the **Command Line Interface (CLI)**.
Switch configuration is generally done through:

* Console Cable
* Telnet
* SSH

Cisco switches operate in different command modes.

---

# Switch Command Modes

| Mode                         | Prompt                 | Purpose               |
| ---------------------------- | ---------------------- | --------------------- |
| User EXEC Mode               | `Switch>`              | Basic monitoring      |
| Privileged EXEC Mode         | `Switch#`              | Administrative access |
| Global Configuration Mode    | `Switch(config)#`      | Device configuration  |
| Interface Configuration Mode | `Switch(config-if)#`   | Interface setup       |
| Line Configuration Mode      | `Switch(config-line)#` | Console/VTY settings  |

---

# 1. Basic Access Commands

## Enter Privileged Mode

```
enable
```

## Exit to User Mode

```
disable
```

## Enter Global Configuration Mode

```
configure terminal
```

## Exit Configuration Mode

```
exit
```

## Return to Privileged Mode Directly

```
end
```

---

# 2. Basic Switch Configuration

## Set Switch Hostname

```
hostname Switch1
```

---

## Set Enable Password

```
enable password cisco
```

## Set Encrypted Enable Secret

```
enable secret class
```

---

## Encrypt Passwords

```
service password-encryption
```

---

## Add Banner Message

```
banner motd # Unauthorized Access Prohibited #
```

---

# 3. Interface Configuration Commands

## Enter Interface Mode

```
interface fastethernet 0/1
```

or

```
interface gigabitethernet 0/1
```

---

## Enable Interface

```
no shutdown
```

## Disable Interface

```
shutdown
```

---

## Assign Description

```
description Connected_to_PC1
```

---

## Set Interface Speed

```
speed 100
```

---

## Set Duplex Mode

```
duplex full
```

---

# 4. VLAN Configuration Commands

## Create VLAN

```
vlan 10
name SALES
```

---

## Assign Port to VLAN

```
interface fastethernet 0/2
switchport mode access
switchport access vlan 10
```

---

## Show VLAN Information

```
show vlan brief
```

---

# 5. Trunk Configuration

## Enable Trunk Port

```
interface gigabitethernet 0/1
switchport mode trunk
```

---

## Allow Specific VLANs

```
switchport trunk allowed vlan 10,20
```

---

## Show Trunk Information

```
show interfaces trunk
```

---

# 6. Switch IP Address Configuration

## Assign Management IP

```
interface vlan 1
ip address 192.168.1.2 255.255.255.0
no shutdown
```

---

## Configure Default Gateway

```
ip default-gateway 192.168.1.1
```

---

# 7. Port Security Commands

## Enable Port Security

```
switchport port-security
```

---

## Set Maximum MAC Addresses

```
switchport port-security maximum 2
```

---

## Sticky MAC Address

```
switchport port-security mac-address sticky
```

---

## Violation Mode

```
switchport port-security violation shutdown
```

---

## Verify Port Security

```
show port-security
```

---

# 8. Console Password Configuration

```
line console 0
password cisco
login
```

---

# 9. Telnet Configuration

```
line vty 0 4
password cisco
login
```

---

# 10. SSH Configuration (Secure Remote Access)

```
hostname Switch1
ip domain-name network.com
crypto key generate rsa
username admin password admin123
line vty 0 4
login local
transport input ssh
```

---

# 11. Saving Configuration

## Save Running Configuration

```
copy running-config startup-config
```

or

```
write memory
```

---

# 12. Show Commands (Verification Commands)

## Show Running Configuration

```
show running-config
```

## Show Startup Configuration

```
show startup-config
```

## Show Interfaces Status

```
show interfaces status
```

## Show MAC Address Table

```
show mac address-table
```

## Show IP Interface

```
show ip interface brief
```

## Show Version

```
show version
```

---

# 13. Reload and Reset Commands

## Restart Switch

```
reload
```

---

## Erase Configuration

```
erase startup-config
```

---

## Delete VLAN Database

```
delete vlan.dat
```

---

# 14. Useful Navigation Shortcuts

| Shortcut   | Function                |
| ---------- | ----------------------- |
| `Tab`      | Auto-complete command   |
| `?`        | Show available commands |
| `Ctrl + C` | Cancel command          |
| `Ctrl + Z` | Exit configuration mode |
| `Up Arrow` | Previous command        |

---

# Switch Configuration Workflow

```
enable
configure terminal
hostname Switch1
interface vlan 1
ip address 192.168.1.2 255.255.255.0
no shutdown
ip default-gateway 192.168.1.1
copy running-config startup-config
```

---

# Conclusion

Switch configuration involves:

* Basic setup
* Interface configuration
* VLAN management
* Security configuration
* Remote access setup
* Verification and maintenance

Understanding these commands is essential for network administration and Cisco networking environments.




# Router Commands (Cisco Router CLI)

---

## Introduction

Routers are configured using the **Cisco IOS Command Line Interface (CLI)**.
Configuration can be done through:

* Console connection
* Telnet
* SSH

---

# Router Command Modes

| Mode                      | Prompt                   | Purpose                |
| ------------------------- | ------------------------ | ---------------------- |
| User EXEC Mode            | `Router>`                | Basic monitoring       |
| Privileged EXEC Mode      | `Router#`                | Administrative control |
| Global Configuration Mode | `Router(config)#`        | Device configuration   |
| Interface Mode            | `Router(config-if)#`     | Interface settings     |
| Line Mode                 | `Router(config-line)#`   | Console/VTY setup      |
| Router Mode               | `Router(config-router)#` | Routing protocols      |

---

# 1. Basic Access Commands

## Enter Privileged Mode

```
enable
```

## Exit to User Mode

```
disable
```

## Enter Global Configuration Mode

```
configure terminal
```

## Exit Configuration Mode

```
exit
```

## Return to Privileged Mode

```
end
```

---

# 2. Basic Router Configuration

## Set Hostname

```
hostname Router1
```

---

## Set Enable Password

```
enable password cisco
```

## Set Encrypted Enable Secret

```
enable secret class
```

---

## Encrypt Passwords

```
service password-encryption
```

---

## Configure Banner Message

```
banner motd # Authorized Users Only #
```

---

# 3. Interface Configuration

## Enter Interface Mode

```
interface gigabitethernet 0/0
```

or

```
interface fastethernet 0/0
```

---

## Assign IP Address

```
ip address 192.168.1.1 255.255.255.0
```

---

## Enable Interface

```
no shutdown
```

---

## Disable Interface

```
shutdown
```

---

## Add Interface Description

```
description Connected_to_LAN
```

---

# 4. Configure Serial Interface (WAN)

```
interface serial 0/0/0
ip address 10.0.0.1 255.255.255.252
clock rate 64000
no shutdown
```

---

# 5. Configure Default Gateway / Static Route

## Default Route

```
ip route 0.0.0.0 0.0.0.0 192.168.1.254
```

---

## Static Route

```
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

---

# 6. Dynamic Routing Protocol Commands

---

## RIP Configuration

```
router rip
version 2
network 192.168.1.0
no auto-summary
```

---

## OSPF Configuration

```
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
```

---

## EIGRP Configuration

```
router eigrp 100
network 192.168.1.0
no auto-summary
```

---

# 7. Configure DHCP Server

```
ip dhcp pool LAN
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 8.8.8.8
```

---

# 8. NAT Configuration

## Enable NAT Inside

```
interface gigabitethernet 0/0
ip nat inside
```

## Enable NAT Outside

```
interface gigabitethernet 0/1
ip nat outside
```

## NAT Overload (PAT)

```
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 interface gigabitethernet 0/1 overload
```

---

# 9. Console Password Configuration

```
line console 0
password cisco
login
```

---

# 10. Telnet Configuration

```
line vty 0 4
password cisco
login
```

---

# 11. SSH Configuration (Secure Remote Access)

```
hostname Router1
ip domain-name network.com
crypto key generate rsa
username admin password admin123
line vty 0 4
login local
transport input ssh
```

---

# 12. Save Configuration

## Save Running Config

```
copy running-config startup-config
```

or

```
write memory
```

---

# 13. Verification Commands (Show Commands)

## Show Running Configuration

```
show running-config
```

## Show Startup Configuration

```
show startup-config
```

## Show IP Interface Brief

```
show ip interface brief
```

## Show Routing Table

```
show ip route
```

## Show Interfaces

```
show interfaces
```

## Show Version

```
show version
```

---

# 14. Troubleshooting Commands

## Test Connectivity

```
ping 192.168.1.2
```

## Trace Route

```
traceroute 192.168.1.2
```

---

# 15. Reset and Reload Commands

## Restart Router

```
reload
```

## Erase Startup Configuration

```
erase startup-config
```

---

# 16. Useful Shortcuts

| Shortcut   | Function         |
| ---------- | ---------------- |
| `Tab`      | Auto-complete    |
| `?`        | Help             |
| `Ctrl + C` | Cancel command   |
| `Ctrl + Z` | Exit config mode |
| Up Arrow   | Previous command |

---

# Basic Router Configuration Workflow

```
enable
configure terminal
hostname Router1
interface gigabitethernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
ip route 0.0.0.0 0.0.0.0 192.168.1.254
copy running-config startup-config
```

---

# Conclusion

Router configuration includes:

* Basic setup
* Interface addressing
* Routing configuration
* Remote management
* Security setup
* Verification and troubleshooting

These commands form the foundation of Cisco router administration and CCNA-level networking.

