# Ansible-playbooks_and_ad-hoc-commands

## Introduction

Ansible is an open-source automation tool that allows you to define and manage infrastructure as code. It uses a simple and human-readable language to describe tasks and configurations, making it easy to automate repetitive tasks, deploy applications, and manage system configurations.

This repository serves as a collection of Ansible playbooks and ad-hoc commands that can be used for a wide range of purposes, including provisioning servers, configuring network devices, deploying applications, and more. 
These resources are intended to provide practical examples and serve as a starting point for automating your own infrastructure.

## Playbooks
The playbooks directory contains a collection of Ansible playbooks that automate different tasks. 
Each playbook is designed to perform a specific function, such as server provisioning, application deployment, or system configuration. 
Refer to the individual playbook's documentation for detailed instructions on usage and customization.

## Ad-Hoc Commands
The ad-hoc-commands directory contains a set of ad-hoc commands that can be run directly from the command line without the need for a playbook. 
These commands provide quick and one-time actions to be performed on remote systems. 
Detailed instructions for using each ad-hoc command can be found in their respective documentation.

# Ansible Playbook Execution Methods

## Running Without Inventory File

### Method 1: Simple IP/Hostname
```bash
ansible-playbook -i "192.168.1.100," ubuntu-docker-setup.yml --user your-username --ask-become-pass
```

### Method 2: With SSH Key Authentication
```bash
ansible-playbook -i "192.168.1.100," ubuntu-docker-setup.yml --user your-username --private-key ~/.ssh/your-key.pem --become
```

### Method 3: With SSH Details Inline
```bash
ansible-playbook -i "your-username@192.168.1.100:22," ubuntu-docker-setup.yml --ask-become-pass
```

### Method 4: Multiple Servers Inline
```bash
ansible-playbook -i "192.168.1.100,192.168.1.101," ubuntu-docker-setup.yml --user your-username --ask-become-pass
```

### Method 5: With Connection Variables
```bash
ansible-playbook -i "192.168.1.100," ubuntu-docker-setup.yml \
  --user your-username \
  --ask-become-pass \
  --ssh-extra-args="-o StrictHostKeyChecking=no"
```

---

## AWS EC2 Instance Specific Methods

### Method 1: Using EC2 Public IP with Key Pair
```bash
ansible-playbook -i "ec2-user@3.15.123.45," ubuntu-docker-setup.yml \
  --private-key ~/.ssh/your-ec2-key.pem \
  --become \
  --ssh-extra-args="-o StrictHostKeyChecking=no"
```

### Method 2: Using EC2 Public DNS
```bash
ansible-playbook -i "ec2-3-15-123-45.us-east-2.compute.amazonaws.com," ubuntu-docker-setup.yml \
  --user ec2-user \
  --private-key ~/.ssh/your-ec2-key.pem \
  --become
```

### Method 3: Ubuntu EC2 Instance (default ubuntu user)
```bash
ansible-playbook -i "ubuntu@3.15.123.45," ubuntu-docker-setup.yml \
  --private-key ~/.ssh/your-ec2-key.pem \
  --become \
  --ssh-extra-args="-o StrictHostKeyChecking=no"
```

### Method 4: Amazon Linux EC2 Instance
```bash
ansible-playbook -i "ec2-user@3.15.123.45," ubuntu-docker-setup.yml \
  --private-key ~/.ssh/your-ec2-key.pem \
  --become \
  --ssh-extra-args="-o StrictHostKeyChecking=no"
```

### Method 5: EC2 with Custom SSH Port
```bash
ansible-playbook -i "ubuntu@3.15.123.45:2222," ubuntu-docker-setup.yml \
  --private-key ~/.ssh/your-ec2-key.pem \
  --become \
  --ssh-extra-args="-o StrictHostKeyChecking=no"
```

### Method 6: Multiple EC2 Instances
```bash
ansible-playbook -i "3.15.123.45,3.15.123.46,3.15.123.47," ubuntu-docker-setup.yml \
  --user ubuntu \
  --private-key ~/.ssh/your-ec2-key.pem \
  --become \
  --ssh-extra-args="-o StrictHostKeyChecking=no"
```

### Method 7: EC2 with Bastion Host (Jump
