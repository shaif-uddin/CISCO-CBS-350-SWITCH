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
no ip domain-lookup
hostname S1
line console 0
logging synchronous
exit
banner motd $ Authorized Access Only! $
exit
copy running-config startup-config
```
