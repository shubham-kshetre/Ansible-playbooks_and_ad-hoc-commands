# This ansible playbook is useful to configure a ubuntu server for:
+ Update and upgrade package
+ install and setup docker engine
+ install and sestup docker compose
+ provide sudo privileges to docker user using 'sudo chmod 666 /var/run/docker.sock'

To use this playbook:

Save it as ubuntu-docker-setup.yml
Create an inventory file with your Ubuntu servers:
```[ubuntu_servers]
   your-server-ip ansible_user=your-username
```
Run the playbook:
```ansible-playbook -i inventory ubuntu-docker-setup.yml
```

