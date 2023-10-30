# ubuntu-services Packer build

## Synopsis

I use a simple packer community-supported builder (`proxmox-iso`) for creating a Proxmox VM template named `ubuntu-services` based on a Ubuntu Server 22.04.2 image.

This Proxmox template has an ID of `300` and `cloud-init` support enabled.  `cloud-init` is used to instantiate basic VM configuration (SSH Public Key, IP, Gateway, DNS, Username) after the VM is created from the template.

## Notes

* Packer uses template **communicators** to upload files, execute scripts etc. with a machine being created. n this case, we use a SSH connection and supply an SSH key (`ssh_private_key_file`) instead of generating it.
* Packer executes `boot` commands after 15s. Part of it instructs an `autoinstall` command.
* An `autoinstall` HTTP server is used on the workstation for unattended OS installation on the virtual disk when building the Proxmox template. This sets values from a `cloud-init` configuration file called  `user-data.yml` .
* After the OS is installed, Packer executes a few shell `provisioners` to wait for `cloud-init` boot to finish on the VM, enable it for future VMs, 
* Lastly, Proxmox VM template is created after provisioning.
* Docker will be installed via Ansible later.

## Packer CLI - Primary commands

To validate the template:

```shell
packer validation -var-file='credentials.pkr.hcl` ./ubuntu-services.pkr.hcl
```

To build the Proxmox VM template:

```shell
packer build -var-file='credentials.pkr.hcl` ./ubuntu-services.pkr.hcl
```  

## Resources

* https://developer.hashicorp.com/packer/plugins/builders/proxmox/iso (Packer builder)
* https://developer.hashicorp.com/packer/docs/communicators/ssh (Packer SSH communicator)
* https://ubuntu.com/server/docs/install/autoinstall (Autoinstall wiki from Canonical)
*  https://pve.proxmox.com/wiki/Cloud-Init_FAQ 
* https://pve.proxmox.com/wiki/Cloud-Init_Support

  