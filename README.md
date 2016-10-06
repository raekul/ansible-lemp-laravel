# LEMP Debian

Just some brief overview stuff for setting up ansible on debian
specifically Ubuntu 14.04/16.04 LTS.

## Prerequisites

You'll need to make sure the following is instaled on your
host machine.

- VirtualBox
- Vagrant

## Once Installed

When you have installed the previous you need to create a 
vagrant/virtualbox instance on a ubuntu based system.

When that's setup you then need to SSH in to the box `vagrant ssh`
as we'll be installing everything and testing our Ansible setup 
here.

## Install the following

```
# Install Python / ansible
sudo apt-get install -y software-properties-common
sudo add-apt-repository -y ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
```

## Running Ansible

```bash
cd ~/path/to/deploy-dist

# Check our Yaml Syntax

ansible-playbook --private-key=~/.ssh/id_testapp \
-i hosts \
--syntax-check \
provision.yml

# Run Everything!

ansible-playbook --private-key=~/.ssh/.pem \
-i hosts \
provision.yml

# Or, Limit runs by host
# In this example, we run only load_balancer tasks

ansible-playbook --private-key=~/.ssh/fideloperllc.pem \
-i hosts --limit=load_balancer \
provision.yml
```