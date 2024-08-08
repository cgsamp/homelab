# Samp Lab

This homelab is used to play with virtualization and container automation.



| Service | URL | Description | Credentials |
|-|-|-|-|
|vCenter|<https://vcenter.lab.sampsoftware.net> | VMware vCenter to manage the SDDC | administrator@vsphere.local / Long|
| Bastion | bastion.lab.sampsoftware.net | Ubuntu host on Lab network |
| Operations Manager | <https://opsman.tas.lab.sampsoftware.net> | Tanzu Operations Manager to manage Cloud Foundry - note login fails but then can refresh| admin / in password manager |
| TAS Apps Manager | <https://apps.system.tas.lab.sampsoftware.net> | Applications Manager | admin / |
| TAS Apps Domain | *.apps.tas.lab.sampsoftware.net | Application hosting wildcard domain |
| TAS System Domain | *.system.tas.lab.sampsoftware.net | System components





# Hardware

## [Poweredge](poweredge.md)

The Lab is based on a Dell PowerEdge T620, current in approximately 2013. It has an older processor ("Xeon Sandy Bridge E5-2640") that is no longer officially supported, but still largely works. It has 256mb DDR2 RAM and 10TB of drive space, some HDD and some SDD, mostly limited by the SATA interface speed. It also has a Ubiquity USG and 8-port router. **Update** Tanzu Application Service runs fine, deploying Spring applications. I cannot install a Windows VM -- I suspect due to the processor but not completely certain.

## [Unifi](unifi.md)

A Unifi router provides the software defined networking. UDM Pro.

## [IP Space](lab-ip-space.md)

Since there is no NSX, the Software Defined Networking capabilities are basic. The 172.16.x.x space is given manually to various services.


## [Virtualization and Services](virtualization.md)


The server has ESXi installed and hosts the current version of vSphere 8. NSX is not installed because it may not be compatibile with the processor. The Ubiquity network device is able to provide VLAN space on the 172.16.x.x IP range, so all network needs just run on that same network.


# Lab VMs

### [Microceph](microceph.md)

There are Ubuntu and Windows bastions running needed services, including PiHole DNS and the Unifi network management software. A Ubuntu Server hosts Microceph to provide S3-compatible storage.


# Tanzu Application Service

TAS / Clound Foundry is a major installation on the Lab. Currently TAS 4 Small Footprint runs. Small Footprint has identical code and services, but requires much fewer VMs as some services are either not deployed or packed more densely on single VMs.

### [Installing TAS](tas-application-service.md)
### [Installing Tiles](tas-tiles.md)
### [Deploying Spring apps](spring-apps.md)
