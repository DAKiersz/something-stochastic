# Ansible - Useful Commands

## Ping all hosts (using hosts file)

You ping targets to check if SSH connectivity is correct.

```shell
ansible -m ping all
```

`-m` is the the module. Notice the `all` at the end - this is the host group.

## Ping specific inventory

```shell
ansible -m ping -i ../config/inventories/prod/hosts all
```

## Ping specific host, with a specific public key

```shell
ansible example -m ping -u [username] --key-file ~/.ssh/id_pub
```

The host group is `example` and `-u` is an extra argument added to this ad-hoc command.

## Send a different command to a host

```shell
ansible example -a "free -m" -u [username]
```

## Install community.docker with ansible-galaxy

Ansible-galaxy is a collection of community maintained roles. Useful for deploying and managing Docker containers.

```shell
ansible-galaxy collection install community.docker
```
