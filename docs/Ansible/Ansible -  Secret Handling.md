# Ansible - Secret Handling

We use ansible-vault to handle secrets.

```
ansible-vault create secret.yml
```

This creates an encrypted `secrets.yml` file that stores any sensitive information. To edit an existing secrets file.

```
ansible-vault edit secret.yml
```

When running a playbook what relies on vault files, add the following arguments.

```
ansible-playbook playbook.yml -K --ask-vault-pass -i inventories/hosts
```

* `-K` ask for the `sudo` password if required by the playbook 
	* If you enabled password less sudo on the machine, we don't need this.
	* The Packer template used in my homelab [[ubuntu-services Packer build]] contains the following line in the `AutoInstall file -> users -> services`:  `sudo: ALL=(ALL) NOPASSWD:ALL`  and so the password is not required for `sudo` commands.
* `--ask-vault-pass` ask for vault password