# APC Powerchute Install

## Synopsis

This guide is my reference to how to install install Powerchute to connect with my UPS. I would ideally do this in `/tmp/` instead. 

1)  Connect to your Proxmox console via root (or a user with `sudo` priviledges)
2) `mkdir /opt/powerchute`
3) `cd /opt/powerchute`
4) `curl "https://download.schneider-electric.com/files?p_enDocType=Software+-+Release&p_File_Name=pcns500Linux-x86-64.tar.gz" -o pcns500Linux-x86-64.tar.gz`
5) `tar -zxvf pcns500Linux-x86-64.tar.gz`
6) `cd Linux_x64`
7) `bash /install.sh`
8) Choose 1 (for English)
9) Install in default `/opt/APC/PowerChute` and confirm
10) username: `apc` and some super secure password
11) Go to port 6547 of the proxmox host
	1) DO not accept CEIP
	2) IPv4
	3) Single UPS configuration
	4) Enter previous password and apc as the user
	5) 12345678901234567890
	6) http and 80  (get this working with https)
	7) wait for connection
	8) Do not turn off the UPS
12) Clear `rm /opt/powerchute`
13) In Powerchute config:
	1) UPS On Battery - 120 UPS On Battery
	2) UPS Temperature Overheated - 0 second delay
	3) UPS Overloaded - 0 second delay

## References

https://www.apc.com/uk/en/product-range/61933-powerchute-network-shutdown/27602445705-powerchute-network-shutdown/?parent-subcategory-id=88978&N=3511179310#software-and-firmware - software website

https://download.schneider-electric.com/files?p_Doc_Ref=SPD_ARAJ-PCNS50LNX_EN&p_enDocType=Software+-+Release&p_File_Name=pcns500Linux-x86-64.tar.gz - direct download for Powerchute Linux v5 (Update 10th June 2023, this is now licenced).

https://www.apc.com/uk/en/product/SFPCNS441/powerchute-network-shutdown-v4-4-1-windows-linux-windows-virtualization-installer-for-nutanix-hyperv-scvmm/ - Verison 4.4.1 with no licence.

https://techexpert.tips/category/apc/ - tutorials
