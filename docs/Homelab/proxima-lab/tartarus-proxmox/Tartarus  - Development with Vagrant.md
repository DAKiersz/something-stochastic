# Tartarus  - Development with Vagrant

## Synopsis

Use a Vagrant box from  https://github.com/rgl/proxmox-ve for development work.

## Setup - tartarus-dev

1) Install everything from the repo above
2) Once packer finishes, add the box as per the link above and run:

```
vagrant up --no-destroy-on-error --provider=virtualbox
```

