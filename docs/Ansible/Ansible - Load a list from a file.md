# Ansible - Load a list from a file

You can load a list from, say, `/install/apt` text file and use it in a task:

```yaml
name: "{{ lookup('file', './install/apt').splitlines() }}"
```