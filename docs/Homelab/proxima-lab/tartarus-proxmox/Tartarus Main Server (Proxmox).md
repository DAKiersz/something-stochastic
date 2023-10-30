# Tartarus Main Server (Proxmox)

## Synopsis

The heart of this server is the Proxmox VE Type I Hypervisor, which will host majority of the services. 

## Install Notes

* Install proxmox on the node.
* Create an active-passive connection for the 10gbit-1gbit failover.
	* That bond should be assigned to the main bridge.
	* Confirm mlx5_core drivers load.
* Fix repository error by disabling the enterprise repository.
* Download CT and ISO templates with Ansible-playbook.
* Create API keys for Packer and Terraform
* Run the Packer build.
* Run the tartarus Infra terraform.
* PCI Passthrough of the LSI card
	* IOMMU issue if necessary - [[Proxmox -  IOMMU Issues]]
	* This will cause problems later.
* USB Passthrough of the backup drive
	* And after adding use the API call to order the USB.
* Create a backup.
	* Wipe the USB disk
	* Create a directory
	* In datacentre view, go to Backup and create daily and monthly backups
	* Mount to fstab /dev/sdc1 /mnt/pve/backup ext4 defaults 0 2
* In the SnipeIT LXC, allow nesting and keyctl (root is required).
	* Run the ansible playbook

## Configuration with Ansible

TBD

## Infrastructure with Terraform

The core infrastructure on Proxmox node is deployed via Terraform, located in `tartarus/infra`.
Using Terraform, we deploy:

* [[Pihole LXC]] - A LXC Debian 11 container with a Pihole (DNS sinkhole) installed. Deployed from a CT image.
* Snipeit LXC - A LXC Ubuntu 22.04 instance with Docker, containing inventory software
* [[TrueNAS VM]] - A TrueNas VM, connected to an LSI HBA adapter, which itself is connected to two Seagate EXOs drives that will server in RAID 1. Deployed from an ISO.
* A Ubuntu Server VM, deployed from a Proxmox VM template build from: [[ubuntu-services Packer build]]

### CLI Reminder

* `terraform plan` and `terraform apply` as per usual to deploy.
* DANGEROUS: `terraform destroy` is used to completely destroy infrastructure, **including disks**.

## Resources

TBD