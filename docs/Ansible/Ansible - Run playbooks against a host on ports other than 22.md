# Ansible - Run playbooks against a host ports other than port 22

## CLI

```shell
ansible-playbook runbook.yml --check -e ansible_ssh_port=2222
```

## Hosts File

You can also edit your host file to introduce the non-standard port:

### Example 1

```
[test]
192.168.1.60 ansible_user=me ansible_port=2222
```

### Example 2

Set the hostname to have the format ‘server:port’ 

```
[test]
192.168.1.60:2222 ansible_user=me
```

### Example 3

```
[test]
192.168.1.60

[test:vars]
ansible_port=2222
ansible_user=me
```

## References

https://linuxfreelancer.com/ansible-non-standard-ssh-port