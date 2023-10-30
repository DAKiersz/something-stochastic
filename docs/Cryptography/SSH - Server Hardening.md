# SSH - Server Hardening

To harden our server and disable password authentication, login to the server and in `/etc/ssh/ssh_config` file ensure you have the following lines:

```
PasswordAuthentication no
ChallengeResponseAuthentication no
UsePAM no
```