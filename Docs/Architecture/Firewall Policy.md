
## Purpose

The purpose of this firewall policy is to outline the requirements for the configuration, management, monitoring, and maintenance of this lab network. 

The policy establishes a consistent approach to firewall management based on principle of least privilege, defence in depth, and default-deny access.

____

## General Policy Statemets

1. Default Deny - Traffic should be denies unless explicitly allowed by a firewall rule.

2. Least Privilege - Rules should only allow the protocols, ports, sources, and destination which are required for legitimate operational purposes.

3. Inbound traffic - Unsolicited connections to internal systems are prohibited.

4. Outbound traffic - Should only be allowed when required and may be restricted by application, destination, or category.

5. Firewall administration - Administrative access is restricted to authorized administrators from designated management networks.

6. Logging - Denied traffic and security-relevant outbound traffic should be logged and monitored.

7. Reviewing rules - Firewall rules should be reviewed periodically and updated frequently so that only required rules are in place.

8. Change control - Permanent rule changes require authorization and documentation.


____

## Traffic Flow Table

* *Inbound - Default Deny*
* *Outbound - Default Deny*

| **Source** | **Destination**   | **Service**                        | **Action**           | **Purpose**                               |
| ---------- | ----------------- | ---------------------------------- | -------------------- | ----------------------------------------- |
| Users      | Internet          | Required outbound services         | Allow, if configured | Internet connectivity from User network   |
| Users      | Servers           | Specified required services        | Allow, if configured | Application Access                        |
| Guests     | Servers           | Specified required services        | Allow, if configured | Application Access                        |
| Guests     | Internet          | Required outbound services         | Allow, if configured | Internet connectivity from Guest network  |
| Management | Network           | Authorized administrative services | Allow, if configured | Network infrastructure administration<br> |
| LAN        | Internal Networks | Lab administrative services        | Allow, if configured | Enables lab admin & troubleshooting       |
| LAN        | Internet          | Required outbound services         | Allow, if configured | Required internet access                  |

For specific firewall rules see [OPNsense](/Docs/Implementation/OPNsense.md).