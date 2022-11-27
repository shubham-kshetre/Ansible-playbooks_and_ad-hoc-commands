# Ansible ad hoc commands  

> Ansible ad hoc commands are one-liner Linux shell commands.
> Ansible ad hoc commands come handy when you want to perform a quick task.

- Check availabality of machine using ping module:

`ansible -m ping localhost`

- To Check uptime

`ansible localhost -m shell -a uptime`
