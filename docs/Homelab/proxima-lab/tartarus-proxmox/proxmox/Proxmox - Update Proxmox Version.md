# Proxmox - Update Proxmox Version

1) Add the following to: `/etc/apt/sources.list` if it does not exist. This is the repository for or no-subscription users i.e., community edition:

```
deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription
```

Bonus: Remove the Proxmox VE Enterprise Repository if it does not exist.

2) Comment out the following line from `/etc/apt/source.list.d/pve-enterprise.list`

```
https://enterprise.proxmox.com/devian/pve
```

3) Upgrade the system via `apt`

```shell
apt update
apt dist-upgrade # apt full-upgrade
```

4) Check pveversion with the following command:

```shell
pveversion
```

## Resources

* https://pve.proxmox.com/pve-docs/chapter-sysadmin.html#sysadmin_package_repositories (Package repositories)

### Standard Community `/etc/apt/sources.list` 

```
deb http://ftp.us.debian.org/debian bullseye main contrib
deb http://ftp.us.debian.org/debian bullseye-updates main contrib
deb http://security.debian.org/debian-security bullseye-security main contrib
deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription
```