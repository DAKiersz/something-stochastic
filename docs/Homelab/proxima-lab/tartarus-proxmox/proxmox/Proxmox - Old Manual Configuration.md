# Proxmox - Old Manual Configuration

## Storage Notes

I previously 

* Via RAID 1 (Mirror) with lz4 compression on both EXOs drives
* Sabrient with LVM-Thin to 1TB
* SMART checking with `smartctl -a /dev/sdx`

Create a mountpoint for exos-raid1 pool. Create a zfs mountpoint with:

`zfs create -o mountpoint=/mnt/exos-raid1 (mountpoint on host) (pool name)/EXOS-RAID1 (mountpoint/dataset name)``

Then you can:

`zfs list`

* First item will be the **pool mountpoint**, second one is the one you created.
* You can check zfs mountpoint with `zfs get mountpoint` 
* Check links to unmount and destroy dataset.
* `chown -R 1005:1005 /mnt/exos-raid1` for a new userid