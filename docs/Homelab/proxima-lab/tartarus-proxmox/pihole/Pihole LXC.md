# Pihole LXC

## Synopsis

A Proxmox LXC running Debian 11, acting as a host for a Pihole DNS sinkhole. 

## Installation Notes

* Run the tartatus terraform template to create the Debian LXC container
* Run the ansible pre-configuration playbook - for all upgrade and a new user.
* SSH into: `curl -sSL https://install.pi-hole.net | bash`
* For the pihole dashboard, create a new password `pihole -a -p`

## Block Lists

Approx. 1.4 million patterns as of 15th July 2023

[blocklistproject/Lists: Primary Block Lists (github.com)](https://github.com/blocklistproject/Lists#usage)
[Blocklist Collection ¦ Firebog](https://firebog.net/)

## Resources

* https://dev.to/jldohmann/the-ultimate-ad-blocker-configuring-pi-hole-with-unbound-dns-20eo (general tutorial)
* https://www.datahoards.com/installing-pi-hole-inside-a-proxmox-lxc-container/ (Installing inside an LXC container)
*  https://www.reddit.com/r/pihole/comments/x7wns0/pihole_hardening_tips_4fun/ (hardening pihole install;)