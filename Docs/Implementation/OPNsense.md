
## Interfaces



| **Interface Name** | **Virtualbox Network** | **Device** | **Interface IP Assignment** | **DHCP Enabled** |
| ------------------ | ---------------------- | ---------- | --------------------------- | ---------------- |
| WAN                | NAT                    | em0        | DHCP                        | No               |
| LAN                | intnet                 | em1        | Static IPv4                 | Yes              |
| Servers            | Servers                | em2        | Static IPv4                 | Yes              |
| Users              | Users                  | em3        | Static IPv4                 | Yes              |
| Management         | MGMT                   | em4        | Static IPv4                 | Yes              |
| Guests             | Guest                  | em5        | Static IPv4                 | Yes              |

## Firewall Rules

**Coming next**

| **Rule ID** | **Direction** | **Source** | **Source Port** | **Destination** | **Destination Port** | **Action** | **Log** |
| ----------- | ------------- | ---------- | --------------- | --------------- | -------------------- | ---------- | ------- |
|             |               |            |                 |                 |                      |            |         |

## Config Notes

### Interface IP assignment

The WAN interface receives its IP address from Virtualbox's NAT DHCP. All of the internal network interfaces are assigned static IPv4 addresses and have their own DHCP pools enabled for any machines are connected to them. 

### DHCP

DNSmasq DNS & DHCP is used in this lab for the following reasons: 
- **Scale:** The lab contains a relatively small number of networks and endpoints.
- **Operational simplicity:** Minimizing infrastructure components makes the initial environment easier to configure, troubleshoot, and document.
- **Integration:** DNS and DHCP can be provided as part of the existing OPNsense infrastructure.


![](/main/Images/DHCP-enabled-interfaces.png)

![](/main/Images/DHCP-ranges.png)
