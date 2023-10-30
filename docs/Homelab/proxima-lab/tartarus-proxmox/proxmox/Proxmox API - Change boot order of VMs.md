# Proxmox API -Change boot order of VMs

Manually define the boot order using Proxmox API

```
pvesh create /nodes/tartarus/qemu/201/config --boot "order=scsi0;ide2;net0"
```

If you cannot shutdown the VM due to `lock-201.conf` do the following. This is really not recommended.

```
rm /var/lock/qemu-server/lock-201.conf
qm stop
```

## Other CLI

https://pve.proxmox.com/wiki/Command_Line_Tools

## References

https://pve.proxmox.com/pve-docs/api-viewer/index.html#/nodes/{node}/qemu/{vmid}/config (Proxmox API)


