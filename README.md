# Playbook to build VM on RHEL Satellite given information from ServiceNow 

Requires: infoblox-client python library, i.e. "pip install infoblox-client"
          PyVmomi python library, i.e. "pip install PyVmomi"

# Playbooks

create-vms.yml - Main playbook - will be modularized later.  Takes a list of new, non-existing VMs and will create them as RHEL8.3 systems in the library-el8 hostgroup
clear_dns.yml - Clean up playbook - will take a list of VMs and clear their DNS records out of DDI
clear_idm.yml - Clean up playbook - will take a list of VMs and clear them from IDM East
clear_satellite - Clean up playbook - will take a list of VMs and delete them from the East Satellite
vm_change_vlan.yml - Will migrate VMs from the build network to gen pop

No delete VM playbook is here... yet.  Deleting VMs using PowerShell is quick but I will include a delete_vm.yml at some point for completeness.

# Group Vars

group_vars/dc1_hosts.yml - contains a number of build parameters for hosts in DC1
group_vars/dc2_hosts.yml - contains a number of build parameters for hosts in DC2

# Playbook usage:

1. create-vms.yml - ansible-playbook -i <inventory> create-vms.yml --ask-vault-pass
	- the inventory file will contain the new hosts you'd like built
	- this playbook will prompt you for your AD username and password to interface with both VMWare and DDI
	- also requires the vault password for the satellite creds
2. clear_dns.yml - ansible-playbook -i <inventory> clear_dns.yml
	- the inventory file will contain the DNS records you'd like removed.
	- this playbook will also prompt for your AD username/password to interface with DDI
3. clear_idm.yml - ansible-playbook -i <inventory> clear_idm.yml
	- the inventory file will contain the hostnames you'd like removed from IDM
	- this playbook will prompt for your IDM East username and password
4. clear_satellite.yml - ansible-playbook -i <inventory> clear_satellite.yml --ask-vault-pass
	- the inventory file... you get it
  	- will require the Vault password for the satellite creds
5. vm_change_vlan.yml - ansible-playbook -i <inventory> vm_change_vlan.yml
