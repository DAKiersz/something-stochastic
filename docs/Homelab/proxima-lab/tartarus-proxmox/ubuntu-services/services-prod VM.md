# services-prod VM

## Synopsis

A Ubuntu Server production VM hosted on Proxmox. This is a docker host.

## Configuration (Deprecated)

This will be done with Ansible:

* Setup fstab:
	* `192.168.60.4:/mnt/tank/media /mnt/tartarus-media nfs defaults 0 2`
* Set `GRUB_TIMEOUT=300` in `/etc/default/grub`
* Crontab backups to a USB harddrive.
* Apt install:
	* smartmontools
	* docker
	* docker-compose

## Resources

TBD