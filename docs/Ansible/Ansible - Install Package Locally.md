# Ansible - Install packages locally

A simple playbook `install-package.yml` that install's git on the local machine.:

```yaml
- name: "Install packages locally"
  hosts: 127.0.0.1
  connection: local
  become: true
  tasks:
	- name: Install packages
	  ansible.builtin.apt:
		name: git
		state: present
```

To run this playbook execute:

```shell
ansible-playbook install-package.yml --ask-become-pass -v
```

You will  need `--ask-become-pass` to execute sudo commands (`apt` may require that on your host). It helps to set `-v` for verbose.