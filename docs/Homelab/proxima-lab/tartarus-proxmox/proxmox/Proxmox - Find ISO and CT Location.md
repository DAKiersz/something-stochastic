
# Proxmox - Find ISO and CT Location

To find where your VM `.isos `are, execute:

```
find / -name "*.iso"
```

For container template, you can find available template and install them manually

```
# check pveam available
# pveam download local debian-11-standard_11.6-1_amd64.tar.zst
```

and you can find their location:

```
find / -name "*tar.zst"
```

