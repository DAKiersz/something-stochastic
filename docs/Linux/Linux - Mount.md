# Linux - Mount

## Mount a NFS Share

To mount an NFS share to `/mnt/truenas-tank` run:

```shell
sudo mount -v -t nfs4 192.168.60.3:/mnt/tank /mnt/truenas-tank
```

## Unmount

```
unmount /mnt/truenas-tank
```

## showmount

```
showmount 192.168.30.4
```