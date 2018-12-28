# MSR_Test_Repo
This is the test repository for creating an infrastructure with Cloud formation

#Ansible Introduction

Ansible works by configuring client machines from an computer with Ansible components installed and configured.

#Install Ansible

$ sudo apt-get update

$ sudo apt-get install software-properties-common

$ sudo apt-add-repository ppa:ansible/ansible

Press ENTER to accept the PPA addition.

Next, we need to refresh our system's package index so that it is aware of the packages available in the PPA. Afterwards, we can install the software:

$ sudo apt-get update# MSR_Test_Repo
This is the test repository for creating an infrastructure with Cloud formation

#Ansible Introduction

Ansible works by configuring client machines from an computer with Ansible components installed and configured.

#Install Ansible

$ sudo apt-get update

$ sudo apt-get install software-properties-common

$ sudo apt-add-repository ppa:ansible/ansible

Press ENTER to accept the PPA addition.

Next, we need to refresh our system's package index so that it is aware of the packages available in the PPA. Afterwards, we can install the software:

$ sudo apt-get update

$ sudo apt-get install ansible

We now have all of the software required to administer our servers through Ansible.

$ mkdir ~/ansible-php 

Move into the new directory.

$  cd ~/ansible-php/

Create a new file called ansible.cfg and open it for editing using nano or your favorite text editor.

$  nano ansible.cfg

Add in the hostfile configuration option with the value of hosts in the [defaults] group by copying the following into the ansible.cfg file.

$ nano ansible.cfg
[defaults]
hostfile = hosts

Save and close the ansible.cfg file. Next, we'll create the hosts file, which will contain the IP address of the PHP Droplet where we will deploy our application.

$ nano hosts

Copy the below to add in a section for php, replacing your_server_ip with your server IP address and sammy with the sudo non-root user you created in the prerequisites on your PHP Droplet.

[php]
your_server_ip ansible_ssh_user=Prasanna

Save and close the hosts file. Let's run a simple check to make sure Ansible is able to connect to the host as expected by calling the ping module on the new php group.

$ ansible php -m ping
Installing Required Packages

$ nano packages.yml
---
- hosts: php
  sudo: yes

  tasks:

  - name: install packages
    apt: name={{ item }} update_cache=yes state=latest
    with_items:
      - git
      - mcrypt
      - nginx
      - php5-cli
•	      NVM – Version 0.33.2
•	Node – 8.12.0
•	Docker – 18.06 or latest
•	Docker Compose – 1.13 or latest
•	Openssl – latest version

Deoploy the packages

$ ansible-playbook packages.yml --ask-sudo-pass


Set Up SSH Keys
As we mentioned above, Ansible primarily communicates with client computers through SSH. While it certainly has the ability to handle password-based SSH authentication, SSH keys help keep things simple.
Create a New SSH Key Pair
If you do not already have an SSH key pair that you would like to use for Ansible administration, we can create one now on your Ansible VPS.

As the user you will be controlling Ansible with, create an RSA key-pair by typing:
$ ssh-keygen
Configuring Ansible Hosts
Ansible keeps track of all of the servers that it knows about through a "hosts" file. We need to set up this file first before we can begin to communicate with our other computers.

Open the file with root privileges like this:
$ sudo nano /etc/ansible/hosts




$ sudo apt-get install ansible

We now have all of the software required to administer our servers through Ansible.
