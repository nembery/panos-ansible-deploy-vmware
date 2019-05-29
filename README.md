
# PAN-OS Deployment using Ansible and Bootstrapper

This is an example playbook that demonstrates how to use the PAN-OS bootstrapper
utility along with Ansible to deploy a VM Series Firewall in a VMWare environment. 

## Setup

This playbook uses the [PAN-OS Bootstrapper Utility](https://github.com/PaloAltoNetworks/panos-bootstrapper)
to generate a bootstrap archive. To set up the bootstrapper utility see the 
[official docs](https://panos-bootstrapper.readthedocs.io/en/latest/).

In order to run this playbook, you need to download and import the PA-VM-ESX-9.0.1.OVA into your vcenter environment. 
Once imported, conver the resulting VM into a VM-Template.

Edit the inventory/group_vars/all file to reflect your environment. 

## Running

Example output below:
```bash

(venv) host:panos-ansible-deploy-vmware pan$ ansible-playbook -i inventory.local provision-pan-vm.yaml  

PLAY [vmware] *************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************************************************
ok: [localhost]

TASK [provision-pan-vm : include_tasks] ***********************************************************************************************************************************************************************************
included: /Users/pan/projects/panos-ansible-deploy-vmware/roles/provision-pan-vm/tasks/generate_bootstrap.yaml for localhost

TASK [provision-pan-vm : Generate Bootstrap ISO] **************************************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : Set permissions on Bootstrap ISO] ****************************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : include_tasks] ***********************************************************************************************************************************************************************************
included: /Users/pan/projects/panos-ansible-deploy-vmware/roles/provision-pan-vm/tasks/launch_pan_vm.yaml for localhost

TASK [provision-pan-vm : Copy bootstrap archives] *************************************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : Create a virtual machine from a template] ********************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : Configure bootstrap ISO] ****************************************************************************************************************************************************************************
changed: [localhost]

TASK [provision-pan-vm : Power-ON VM-Series] ******************************************************************************************************************************************************************************
changed: [localhost]

PLAY RECAP ****************************************************************************************************************************************************************************************************************
localhost                  : ok=9   changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```


## Support Policy

The code and templates in the repo are released under an as-is, best effort, support policy. These scripts should be 
seen as community supported and Palo Alto Networks will contribute our expertise as and when possible. We do not 
provide technical support or help in using or troubleshooting the components of the project through our normal support 
options such as Palo Alto Networks support teams, or ASC (Authorized Support Centers) partners and backline support 
options. The underlying product used (the VM-Series firewall) by the scripts or templates are still supported, but the 
support is only for the product functionality and not for help in deploying or using the template or script itself. 
Unless explicitly tagged, all projects or work posted in our GitHub repository (at https://github.com/PaloAltoNetworks) 
or sites other than our official Downloads page on https://support.paloaltonetworks.com are provided under the best 
effort policy.