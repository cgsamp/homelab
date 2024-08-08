# IP Networks

|Network name|Uplink IP|Gateway|CIDR|Subnet|IP Range|Management device|Management interface|admin creds|
|-|-|-|-|-|-|-|-|-|
|Xfinity|68.48.x.x|192.168.0.1|24|255.255.255.0|192.168.0.1-192.168.0.254|Xfinity router|https://192.168.0.1 | admin/X |
|Ubiquity Default VLAN 1|192.168.0.100|192.168.1.1|24|255.255.255.0|192.168.1.1-192.168.1.254|Unify web appliance|(on mac)https://127.0.0.1:8080 | Ubiquiti web credential |
|Ubiquity the_lab VLAN 2||172.16.0.1|16|255.255.0.0|172.16.0.1-172.16.255.255|Unifi web appliance|||

## Xfinity

Household 1.2Gbit cable network serving the lab and home use. Ethernet cable runs from the modem to a Netgear switch in the lab closet. One port is connected to the USG WAN port.

192.168.0.1/24

## the_lab

General lab equipment not part of another solution. Services used by several solutions.

### 172.16.0.1/16

|IP or Range|DNS|Assignment|
|-|-|-|
|172.16.0.1 - 1 | Gateway |
|172.16.0.2 - .29 | Ad hoc lab services |
|172.16.0.30 - 254 | Lab DHCP |
|172.16.1.100 | esxi-t620.sampsoftware.net |ESXi Host |
|172.16.1.101 | vcenter.sampsoftware.net| vCenter Client |
|172.16.1.102 | pihole.sampsoftware.net | pihole DNS service |
|172.16.1.102 | bastion.sampsoftware.net | Ubuntu desktop bastion |
|172.16.2.2 | opsman.tas.lab.sampsoftware.net | TAS Operations Manager |
|172.16.2.10 | ~~haproxy.tas.lab.sampsoftware.com~~ | Load Balancer for GoRouters
|172.16.3.11 | HAProxy out of the loop now | One GoRouters
| ^ | system.tas.lab.sampsoftware.net | TAS System Domain
| ^ | *.system.tas.lab.sampsoftware.net | TAS Wildcard System Domain |
| ^ | apps.tas.lab.sampsoftware.net | TAS Apps Domain |
| ^ | *.apps.tas.lab.sampsoftware.net | Wildcard TAS Apps Domain |

## lab_tkg_supervisor

### 172.32.3.1/24 management
### 172.32.4.1/24 workload


1.2. Permit Root Login = True
1.3. TLS Certificate Authority Certificate (ca.crt) = 
1.4. TLS Certificate Authority Private Key (ca.key) = 
2.1. Host Name = haproxy.tkg.lab.sampsoftware.net
2.2. DNS = 172.16.1.102,172.16.5.2
2.3. Management IP = 172.16.4.10/24
2.4. Management Gateway = 172.16.0.1
2.5. Workload IP = 172.16.5.10/24
D
2.6. Workload Gateway = 172.16.0.1
2.7. Additional Workload Networks = 
3.1. Load Balancer IP Ranges, comma-separated in CIDR format (Eg 1.2.3.4/28,5.6.7.8/28) = 172.16.6.0/24
3.2. Dataplane API Management Port = 5556
3.3. HAProxy User ID = haproxy

-----BEGIN CERTIFICATE-----
MIIDxzCCAq+gAwIBAgIJAM5LjgRVJQcjMA0GCSqGSIb3DQEBBQUAMIGAMQswCQYD
VQQGEwJVUzETMBEGA1UECAwKQ2FsaWZvcm5pYTESMBAGA1UEBwwJUGFsbyBBbHRv
MQ8wDQYDVQQKDAZWTXdhcmUxDTALBgNVBAsMBENBUFYxKDAmBgNVBAMMH0NJX01J
U1NJTkdfSklOSkFfVkFSL2xvY2FsX2lwdjQwHhcNMjQwNTI5MTk1OTA2WhcNMzQw
NTI3MTk1OTA2WjCBgDELMAkGA1UEBhMCVVMxEzARBgNVBAgMCkNhbGlmb3JuaWEx
EjAQBgNVBAcMCVBhbG8gQWx0bzEPMA0GA1UECgwGVk13YXJlMQ0wCwYDVQQLDARD
QVBWMSgwJgYDVQQDDB9DSV9NSVNTSU5HX0pJTkpBX1ZBUi9sb2NhbF9pcHY0MIIB
IjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAzDH1Sj3USwH1euT3LBJv6uQU
knSUapDuXtNz0myCnDb4NeCwXdk+1Tk+XiF8eFgxCB5dOTW2K3pkfVOMcNKddMaB
pfsUuIa2bJo/Vf67o7VwiH6n+ILFp2L9t4/bYMR71yT3rXiSho6MY6F8NL+6xXW1
UpTPpPAjkK0KUIxF7sOAD1SpzJyKFh9Xa91D5dwy/y4lRSP3bSG1lUk3hSPu09fd
qJrM1zqhBQcu2brxJ0TkGdtgz5oX2lOAvyrzNAwcWIj6g8Ibb5Azz7Z/PEExYKmS
woSJ6pkMWzA5EwdbmDEulMc9CWhJLvtS03ixRYwVh6qIkAu5JJdDK+RMrd8lMQID
AQABo0IwQDAPBgNVHRMBAf8EBTADAQH/MA4GA1UdDwEB/wQEAwIBhjAdBgNVHQ4E
FgQUI+ah4uh3rD6vbbf9oPm01KYqqiEwDQYJKoZIhvcNAQEFBQADggEBACxw4Ykw
0qO8js+UXywziEK+tn4/BRetZbdCNEPigjSrRzd4uh/X1Tt8Vh6gcrUomqEfT/Lg
oUANXXOmzES2R9yybAr689muKgsmX9+qW3ANdXxyd+KtTMshNjsyFW4D145AN0Gx
pCapK7H2EBlWN70tDqT+1DugVkrOu+soLaTHvPQIzDX8cZs48cOXoq6PXG4K21XJ
s09iRQvfRC6cN1vu8ouVbue+UjWoKs3RNDPGU2gzoX78evvQq/wZx7ybGkfY3COw
rPKygMV0nb+q5u8I1h/D8MTcWEXSV4DHNxm/ATCjmAJpadFTRJ/JYbdlkm1nGf6P
ki4yhmu4uIR85uc=
-----END CERTIFICATE-----



|Service|Username|Password type|
|-|-|-
|bastion.sampsoftware.net|cgsamp|short|
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
