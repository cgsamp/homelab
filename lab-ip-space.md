# IP Networks

|Network name|Uplink IP|Gateway|CIDR|Subnet|IP Range|Management device|Management interface|admin creds|
|-|-|-|-|-|-|-|-|-|
|Xfinity|68.48.x.x|192.168.0.1|24|255.255.255.0|192.168.0.1-192.168.0.254|Xfinity router|https://192.168.0.1 | admin/X |
|Ubiquity Default VLAN 1|192.168.0.100|192.168.1.1|24|255.255.255.0|192.168.1.1-192.168.1.254|Unify web appliance|(on mac)https://127.0.0.1:8080 | Ubiquiti web credential |
|Ubiquity the_lab VLAN 2||172.16.0.1|16|255.255.0.0|172.16.0.1-172.16.255.255|Unifi web appliance|||

## Xfinity

Household 1.2Gbit cable network serving the lab and home use. Ethernet cable runs from the modem to a Netgear switch in the lab closet. One port is connected to the USG WAN port.

## Ubiquity Default

The DMZ? This is for services that are within the USG domain but not in the lab. Maybe this is the management network?

## the_lab

This is a very large IP space onto which the various lab systems are deployed. It covers everything from the management interfaces to DHCP spaces and all of the containers needed to support any and all lab systems. In a production scenario this would be served by something more robust like NSX, but I have not yet incorporated that complexity as it is not the focus of this lab.

### the_lab sub networks

I call these "sub networks" as opposed to "subnets" because they are arbitrary definitions I create by assigning different services different IPs. They are all mutually routable with no restriction. Again, this is not what one would expect in a production or production-simulating environment at this particular layer.

|IP or Range|DNS|Assignment|
|-|-|-|
|172.16.0.1 - 1 | Gateway |
|172.16.0.2 - .29 | Ad hoc lab services |
|172.16.0.30 - 254 | Lab DHCP |
|||
|172.16.1.1 - .254 | Named lab services |
|172.16.1.100 | esxi-t620.sampsoftware.net |ESXi Host |
|172.16.1.101 | vcenter.sampsoftware.net| vCenter Client |
|172.16.1.102 | pihole.sampsoftware.net | pihole DNS service |
|172.16.1.102 | bastion.sampsoftware.net | Ubuntu desktop bastion |
|||
|172.16.2.1 - .254 | TAS Services |
| 172.16.2.2 | opsman.tas.lab.sampsoftware.net | TAS Operations Manager |
| 172.16.2.10 | system.tas.lab.sampsoftware.net | TAS System Domain |
| 172.16.2.10 | *.system.tas.lab.sampsoftware.net | TAS Wildcard System Domain |
| 172.16.2.10 | apps.tas.lab.sampsoftware.net | TAS Apps Domain |
| 172.16.2.10 | *.apps.tas.lab.sampsoftware.net | Wildcard TAS Apps Domain |

|Service|Username|Password type|
|-|-|-
|bastion.sampsoftware.net|cgsamp|short|
|esxi host|root|long|
|vcenter|administrator@vsphere.local|long|
|OpsMan|admin|short|




Xfinity cable 1.2gbit


192.168.0.0/24

192.168.0.100

## 

xfinity network - 192.168.0.0/24

ubiquity wan ip = 192.168.0.100 -- configured as static on xfinity

ubuquity default - lab dmz - 192.168.1.0/24

ubiquity lab - the_lab - 172.16.0.0/16
