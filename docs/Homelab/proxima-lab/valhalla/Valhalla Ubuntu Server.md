# Valhalla Ubuntu Server

## Synopsis

A quick setup of a TV Headend Server via Ubuntu 20.04. The host is a Thinkpad T450 and it is connected to a PCTV tripleStick HD 292e TV Tuner.

## Previous Configuration (Deprecated)

This will be done via Ansible

* Allow  SSH
* Install pip and python.
* Install drivers.
* Copy firmware to /lib/firmware
* Install TVheadend (with Docker)
* Disable power to monitor
* Firewall config to allow local network only on TVHeadend ports.

## TODO

* Harden
* Create new user with sudo priviledges, and disable root.
* Add on TLP configuration.

## Resources