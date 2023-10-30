# Vagrant - Basics

A short list of commands for dev work.

## CLI Commands

### up

If you have a Vagrantfile ready in the directory, run:

```shell
vagrant up [--provider=virtualbox] [--no-destroy-on-error]
```

To boot the machine from dir your Vagrantfile is (and if for the first time, then it will also apply the provisioner). Arguments can optionally be set as stated above.

## box 

Add a box.

```
vagrant box add [machine]
``` 

You can use a number of boxes from [Vagrant Cloud](https://app.vagrantup.com/boxes/search) 

Run the following to upgrade the box (for some provider like virtualbox):

```shell
vagrant box update
```

## init

Create a default virtual server configuration using the box your downloaded (via `vagrant box add`)

```
variant init [machine]
```

## destroy

To deprovision the box, run this in the directory Vagrantfile is in.

```shell
vagrant destroy
```

## provision

Apply the provisioner without destroying the VM (e.g., Ansible).

```
vagrant provision
```

### Ansible provisioner

In your Vagrantfile, define

```ruby
config.vm.provision "ansible" do |ansible|
	ansible.playbook = "playbook.yml"
end
```


## Other Commands

`vagrant ssh [name]` - connect to machine

`vagrant ssh-config <>` - specific config for a VM

`vagrant ssh-config > vagrant-ssh` - Generate a ssh config file you can just enter with.
`ssh -F vagrant-ubuntu-ssh ubuntu-server-jammy`

`vagrant global-status` - show all boxes

`vagrant destroy [machine]` - remove the machine

`vagrant plugin install [plugin]` - Install a plugin.