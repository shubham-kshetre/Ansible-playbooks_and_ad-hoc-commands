# Ansible ad hoc commands  

> Ansible ad hoc commands are one-liner Linux shell commands.
> Ansible ad hoc commands come handy when you want to perform a quick task.

- Check availabality of machine using ping module:

`ansible -m ping localhost`

- To Check uptime

`ansible localhost -m shell -a uptime`

- [b]ecome root user and as[k] for sudo password:

`ansible localhost -m shell -a "cat /etc/passwd" -b -K`

- Execute a command as a different user  (sudo su):

`ansible localhost -m shell -a "mkdir {{dir name}}" -b – become-user={{username}}`

- Create a user group:

`ansible localhost  -m group -a "name=newgrp state=present"  -b -K`

- Create a unix user:

`ansible localhost -m user -a "name=newUser group=newUser createhome=yes" -b -K`

- Create a Directory with 777 permission:

`ansible localhost -m file -a "path=/home/shubham/Desktop/newDir state=directory mode=0777" -b -K`
