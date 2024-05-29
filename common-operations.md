# Common Operations

## Connect to Opsman and use BOSH CLI

Operations Manager Director is the first VM created. To access VMs or other SSH-able components, first ssh to the director, and then use the bosh cli.

### SSH to Bosh Director

Ensure the public key is specified.

From your workstation or linux bastion:

ssh ubuntu@[fqdn] -i path/to/publickey

ssh ubuntu@opsman.tas.lab.sampsoftware.net -i secret/id_opsman

### Set environment variables

export BOSH_CLIENT=ops_manager \
BOSH_CLIENT_SECRET=some_secret \
BOSH_CA_CERT=/var/tempest/workspaces/default/root_ca_certificate \
BOSH_ENVIRONMENT=172.16.3.2 bosh

export BOSH_CLIENT=ops_manager \
BOSH_CLIENT_SECRET=eiZWk3ARtNfEkkZc082NbyQ-rbzmxnxn \
BOSH_CA_CERT=/var/tempest/workspaces/default/root_ca_certificate \
BOSH_ENVIRONMENT=172.16.3.2
