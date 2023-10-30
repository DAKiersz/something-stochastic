
# Proxmox VT-d / IOMMU Issue

## Synopsis

On a fresh install of Proxmox, I see the following message when adding a PCIe device to a virtual machine

```
No IOMMU detected, please activate it. See Documentation for further information.
```

This means that VT-d (Virtualisation Technology for Directore I/O) is not activated in BIOS, that the kernel did not pick it up.

## Solution

1) Ensure that  `/etc/defaults/grub` contains the following line after chancing it to bios

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet intel_iommu=on"
```

2) `update-grub` to update grub configuration.

3) `reboot`


## References

https://forum.level1techs.com/t/proxmox-no-iommu-detected-please-activate-it/179947/11