# Local Development with Vagrant

To conduct local development, as to avoid cowboying production, I spin up different VMs using virtualbox and Vagrant. The primary development on those machines is about running Ansible.

* A Proxmox VM - to avoid altering the live Proxmox hypervisor directly.
* A ubuntu-server-jammy - A Ubuntu 22.04.2 machine *similar* to [[ubuntu-services Packer build]] used for hosting Docker container services. It should be noted, we run this on different hardware and without cloud-init.
* A ubuntu-server-focal - A Ubuntu 20.04 machine used for [[Valhalla Ubuntu Server]].
