# Cisco Business 350 Series Managed Switches
## **CBS350-24T-4G Cli Reference commands only**

### Setup
---

#### Intialize
```
erase startup-config
delete vlan.dat
reload
```

#### Basic Switch Config
```
configure terminal
hostname S1
exit
banner motd $ Authorized Access Only! $
exit
copy running-config startup-config
```
#### Basic Security

```
SW(config)# username <username> privilege 15 secret <password>

```
##### Enable telnet
```
line telnet
enable authentication <password>
login
```
#### Set Clock

*Show Clock*

```
# show clock
```

```
clock timezone UTC +6
```

*Create VLANS*
```
conf t
vlan 10
name Management
vlan 20
name Sales
vlan 30
name Operations
end
```
#### Management VLAN
##### Create interface & assing ip 

```
conf t
int vlan 10
ip address 192.168.1.100 255.255.255.0
exit
ip default-gateway 192.168.1.1
```

##### Add interfaces to VLANS, 8 ports per vlan

```
conf t
int range f0/1-7
switchport mode access
switchport access vlan 10

int range f0/8-15
switchport mode access
switchport access vlan 20

int range f0/16-24
switchport mode access
switchport access vlan 30
end
```

#### Trunks

```
conf t
interface Gi0/1
description Trunk Line to S2 Gi0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 99
end
```
#### Trunk Verification
```
show interface trunk
show interface g0/1 switchport
```