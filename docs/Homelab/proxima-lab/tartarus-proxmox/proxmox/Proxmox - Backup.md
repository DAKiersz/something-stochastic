# Proxmox - Backup Restore

## Synopsis

I have backups for VMs and CTs on my USB dirve

1) In Server View > Node > Disk > See 
	1) Command like `fdisk` would work too.
2) To mount the backup

```shell
mkdir /mnt/backup
mount /dev/sdc1 /mnt/backup
```

3) Restore a container with `pct`

```
pct restore 101 /mnt/backup/dump/vzdump-lxc-100-2023_06_09-09_50_22.tar.zst --rootfs local-lvm:8
```

4) Restore a QEMU disk with `qmrestore`

```
qmrestore /mnt/backup/dump/vzdump-qemu-200-2023_06_09-09_53_17.vma.zst 200
```


## Resources

https://pve.proxmox.com/wiki/Backup_and_Restore (official documentation) 

