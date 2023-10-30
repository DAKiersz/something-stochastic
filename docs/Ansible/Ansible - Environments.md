# Ansible - Using different environments

One recommendation is to create separate hosts for each environment, then execute:

```
ansible-playbook my_playbook.yml -i inventories/dev/hosts
ansible-playbook my_playbook.yml -i inventories/prod/hosts
```

This eliminates the need for separate playbooks, and allows for easy execution of the same playbook on different environments.

## References

https://docs.ansible.com/ansible/latest/cli/ansible-playbook.html
https://stackoverflow.com/questions/59786247/best-ansible-layout-with-multiple-environments