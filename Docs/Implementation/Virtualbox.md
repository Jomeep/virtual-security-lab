## Why Virtualbox?

Oracle Virtualbox was chosen as the hypervisor for this project for the following reasons: 
1) Hardware limitations 
2) Prior familiarity with the solution
3) Intuitiveness for setting up machines
## Machine Inventory


| **Machine OS**                        | **Purpose**        | **Attached Network Adapters** |
| ------------------------------------- | ------------------ | ----------------------------- |
| OPNsense / FreeBSD (64-bit)           | Runs OPNsense      | 1-6                           |
| Kali / Ubuntu (64-bit)                | Lab Administration | 2                             |
| Windows 11 (64-bit)                   | Workstation        | 3                             |
| Ubuntu 25.04 (Plucky Puffin) (64-bit) | Server             | 4                             |

___

## Network Adapters


| **Adapter ID** | **Adapter Name** | **Purpose**                       |
| -------------- | ---------------- | --------------------------------- |
| 1              | NAT              | Attached to OPNsense WAN          |
| 2              | intnet           | Attached to LAN                   |
| 3              | Users            | Enables Users segment config      |
| 4              | Servers          | Enables Servers segment config    |
| 5              | MNGT             | Enables Management segment config |
| 6              | Guest            | Enables Guest segment config      |

### Enabling All Required Adapters

By default, Virtualbox supports up to 4 network adapters per machine. However, this number can be increased up to 8. For the purpose of this lab,  the decision was made to add 2 additional network adapters to the OPNsense virtual machine.

**Enabling Additional Adapters:**
```Shell
VBoxManage modifyvm "OPNsense" --nic5 intnet
```


**Name the new network:**
```Shell
VBoxManage modifyvm "OPNsense" --intnet5 "MNGT"
```



**Making sure the correct adapter type is defined:**
```Shell
VBoxManage modifyvm "OPNsense" --nictype5 82540EM
```


**Screenshot from OPNsense VM with all adapters:**
![](network-adapters.png)