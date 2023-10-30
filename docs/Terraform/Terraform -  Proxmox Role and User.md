## Terraform - Proxmox Role and User

Under the principle of least privilege, we would like to create the Proxmox role, and a user for Terraform to use to deploy infrastructure.

We can use following commands to create a role, then a user.

```bash
pveum role add terraform -privs "VM.Allocate VM.Clone VM.Config.CDROM VM.Config.CPU VM.Config.Cloudinit VM.Config.Disk VM.Config.HWType VM.Config.Memory VM.Config.Network VM.Config.Options VM.Monitor VM.Audit VM.PowerMgmt Datastore.AllocateSpace Datastore.Audit"

pveum user add terraform@pve --password <password>

pveum aclmod / -user terraform@pve -role terraform
```

You can then generate an API key for this user.

## References

https://registry.terraform.io/providers/Telmate/proxmox/latest/docs
