# SSH - Configuration File

## Synopsis

The configuration file is a good way to alias all of the SSH settings from your workstation.

## Example

A simple example from my home network:

```
# * valhalla
Host 192.168.30.1
  HostName 192.168.30.1
  Port 48869
  User dakiersz
  IdentityFile ~/.ssh/id_rsa
```