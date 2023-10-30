
# Terraform - Import Existing Resources

## Synopsis

Import existing resources to TF, even if you initially provisioned them with Terraform.

## Description

Import remote resource to your state file (if your provider supports it, this is an example for the truenas provider.

```shell
terraform import truenas_dataset.media "tank/media"
```

Or for `telmate/proxmox` provider

```
terraform import proxmox_vm_qemu.services-prod tartarus/qemu/201
```

---

If Terraform complains about already managing an remote object: `Terraform is already managing a remote object for truenas_dataset.media. To import to this address you must first remove the existing object from the state.`

```shell
terraform state rm truenas_dataset.media
```

Then import the resource state using the first command.

To show the state of a particular resource, that you can copy the configuration for:

```shell
terraform state show truenas_dataset.media
```

The output is the configuration you can copy to your `main.tf`.