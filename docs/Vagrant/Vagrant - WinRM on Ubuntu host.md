# Vagrant - WinRM on Debian host

To get a Windows bpx up on a Debian based system, install the following for WinRM, the communication protocol for Windows machines:

Using `vagrant plugin install` command

```
vagrant plugin install winrm winrm-fs
```

Using `gem` Ruby package manager:

```
sudo gem install winrm winrm-elevated
```

## References

https://github.com/rapid7/metasploitable3/issues/568


