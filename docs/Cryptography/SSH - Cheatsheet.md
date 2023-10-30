# SSH - Cheatsheet

SSH allows to ensure our identity without a password.

Connect to host via SSH, as a specified user.

```shell
ssh remote-user@192.168.1.1
```

Create a SSH private-public pair:

```shell
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519 -C email@gmail.com
```

`-t` - Algorithm type
`-f`  - Output file
`-C`  - Email email@gmail.com
`-a` - Rounds

Copy the public key to a target host (remote-user@192.168.1.1) for the host to trust the key

```shell
ssh-copy-id -i ~/.ssh/id_ed25519 remote-user@192.168.1.1
```

Test connection

```shell
ssh -i ~/.ssh/id_ed25519 remote-user@192.168.1.1
```

Reload the SSH daemon if needed.

```shell
systemctl reload sshd
```

