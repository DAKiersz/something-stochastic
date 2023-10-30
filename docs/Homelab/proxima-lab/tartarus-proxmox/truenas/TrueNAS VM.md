# TrueNAS VM

## Synopsis

The main storage component is a virtualised TrueNAS VM with an LSI HBA connected via PCIe passthrough. 

## VM Installation Notes

* Run tartatus terraform template to create the VM from an ISO.
	* Set 48Gb of RAM and 2 Cores to ensure enough RAM for ZFS.
* Add the LSI card via passthrough manually. There is no Terraform resource block for that.
* From Proxmox, go to the console and install manually.
	* Select only `da0` drive for installation.
* Login to TrueNAS.
* Network > Global Configuration > DNS Server and Gateway.
* Network > Interfaces > Disable DHCP and add the required IP address.
* Create a tank pool in RAID 1 with default settings.
* Create a group/user called `nfsshare`
	* G/PID 3000. 
	* No home directory.
	* No Samba.
* By default, root user is in the `wheel` group. Default datasets have permissions to root/wheel.
	* This needs changing -> Edit Permissions > Edit ACL
* Create a short daily SMART test on tank disks.
* Services > Check NFS and SMART

## API Key

* Go to the settings icon on right hand-side.
* Select API Keys
* Press Add and create a 'terraform' key'

## Configuration

There is a Terraform provider for **datasets** and **nfs shares** that will be done

## Resources

https://opensource.com/article/22/6/terraform-truenas (Using Terraform)
https://registry.terraform.io/providers/dariusbakunas/truenas/latest/docs (Terraform Provider)
https://www.youtube.com/watch?v=ySMitWnNxp4 (NFS)