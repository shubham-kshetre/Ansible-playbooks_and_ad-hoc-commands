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

- To check the service status:

`ansible localhost -m service -a "name=httpd"`

- Use copy module to copy files from local to remote machine:

`ansible remoteserver -m copy -a "src=~/Documents dest=/home/user/ owner=user group=user mode=777"`

- To run script on remote machine using script module:

`ansible localhost -m script -a ./helloWorld.sh -v`

- ad hoc command to list nfs mounts:

`ansible testservers -m shell -a 'df -h -T|grep -i nfs'  -i ansible_hosts`

- Find all the log files older than 30 days with Ansible Find:

`ansible appgroup -i ansible_hosts -m find -a "paths='/var/log' file_type=file patterns='*.log' age_stamp=mtime age=30d"`

- Recursively find the files by Size using Ansible Find:

`ansible localhost -m find -a "paths='/var/log' file_type=file patterns='*.log' size=100m"`
