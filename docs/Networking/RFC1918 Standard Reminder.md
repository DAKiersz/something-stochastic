# RFC1918 Standard Reminder

## Summary

You can use the following IP spaces for your LAN.

 * `192.168.0.0/16`  (subnet that starts with `192.168`)
 * `172.16.0.0/12`  (subnet that starts with `172.16` through `172.31`)
 * `10.0.0.0/8` (subnet that starts with `10.)

Those are RFC1918 addresses (private address spaces that will never be publicly rotatable, not without port forwarding at least...). 

## Classes

Class A Blocks end with "/8" and contain 16 million IP addresses. 
Class B Blocks end with "/16" and contain 65,000 IP addresses. 
Class C Blocks end with "/24" and support a maximum of 254 IP addresses.

## VLANs and Subnet

* In the Networking model, VLANs are at L2. Subnets are at L3. 
* Both VLANs and Subnets limit broadcast domain and implement a concept of traffic separation.
* A nice convention to use in a homelab scenario is to set your VLANs based on a subnet as follows:  `10.1.20.0/24` is on VLAN 20