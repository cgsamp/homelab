# Tanzu Application Service

## Install Opsman

1. Download and deploy OVF
    1. Network settings:
        1. IP: 172.16.2.2
    1. Certificate
    ```
    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCxkPMvcUVR6W5gb9kMgtpkWGBlq9YoEG0atxsnJjHl2SbOvSOlH4sq+jtn53hH+DC0aDEnWMUyyEvABoiBK2hltoWtH6/EUResdzG8o1JcHJoJeXT1zNBKDF72fplgdLUdZfg38XARcKMO3myWulBr3gnF/1O0S+br2ZFZoH314LI9UPs/dfsnPsj2s6Ex2msmmMBX94AwzHKkDAKcc2JF0WVlwKZFTU7PKgcXnvXNQlGUTy3yTyXIjwUrdY1RAPaPUv5S8ptbhH/qcqxXIwX7C+Wsn9mCYEEFhHQTRAZltlnDXnPR1iwN5GSArVNDk+9PHPTZrIL5svOik304qbHPz0dJ893foakdVb7cPLBMO1/wD6yMlfLAD40O9pYdju/l0WJwbqpqPrNLHL6naFumskdH22I/iFMFc21uvAxFUrr76qp2js3HidoEq7HYWpqzNIUv3NVeoGz+QJrx9fX5u4ENv2GLrc3W9BwAq8CnVFHOKKezacuXXxS6Yy7gVL8= cgsamp@ubuntu-bastion
```

    1. IMPORTANT: Be sure to check the Include Opsman CA Certs if you are going to let TAS generate the Gorouter and UAA rsa certs during the TAS install. Otherwise you will be plauged by "untrusted CA" errors and you will generate the TAS certs over and over until you remember this checkbox. Ask me how I know.
   
## Install TAS

Upload .pivotal file.

### Configure Domains

This is a bit circular because you need to have the DNS records created, but the IPs you need are for the routers, that are not yet created. Just plan for them and set them here. See ip space.

If using pihole, it does not support wildcard DNS entries. So you need to create it.
https://www.reddit.com/r/pihole/comments/gpxvy2/how_to_add_a_wildcard_dns_record_on_pihole/
```
cat << EOF > 10-tas.conf
address=/system.tas.lab.sampsoftware.net/172.16.3.10
address=/apps.tas.lab.sampsoftware.net/172.16.3.10
EOF

sudo cp 10-tas.conf /etc/dnsmasq.d/
```
Then restart the DNS service in PiHole under Settings

### Network

#### Gorouter IPs

172.168.3.11 - 172.16.3.15

There are several areas to generate RSA certificates. I should come back and make these with my own CA so I can add it to my trust stores.

Several are needed: --EXACTLY WHICH?
*.apps.tas.lab.sampsoftware.net,*.system.tas.lab.sampsoftware.net,login.system.tas.lab.sampsoftware.net

### Credhub

Key: 012345678901234567890

### UAA

### TEST cf push

1. Try this sample app
1. Or, follow this to begin with start.spring.io to a hello world:



export BOSH_CLIENT=ops_manager \
BOSH_CLIENT_SECRET=some_secret \
BOSH_CA_CERT=/var/tempest/workspaces/default/root_ca_certificate \
BOSH_ENVIRONMENT=172.16.3.3 bosh

