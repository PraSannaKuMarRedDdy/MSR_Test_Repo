## MSR_COSMO Task

***What is ansible-playbooks?****

It is a set of [ansible](http://www.ansible.com/home) playbooks showing you how to create certain full server stacks.

## Prerequisites

First of all, local server should be able to access to remote server over SSH so let's do it.

### Generate SSH keypair on local

ansible@local:~$ ssh-keygen -t rsa

Transferring public key

ubuntu@remote:~$ echo 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDUkN ansible@local' >> ~/.ssh/authorized_keys

Testing SSH connection

ansible@local:~$ ssh ubuntu@192.168.99.30

Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-92-generic x86_64)

## Installation

#### Installing ansible through a self built debian package

You may want to check what the latest stable version of ansible is before copying and running this command. Adjust the version at the end of the command.

`curl -s https://raw.githubusercontent.com/nickjj/ansible-playbooks/master/ansible-install.sh | bash /dev/stdin v1.6.2`

Afterwards verify that ansible is installed by running `ansible --version`.

#### Cloning this repo

`$ git clone https://github.com/nickjj/ansible-playbooks.git`

#### Doing everything as a 1 liner

Goto a directory where you want the playbook to be git cloned and then run this command:

`curl -s https://raw.githubusercontent.com/nickjj/ansible-playbooks/master/ansible-install.sh | bash /dev/stdin v1.6.2 && git clone https://github.com/nickjj/ansible-playbooks.git`

#### File structure break down

            $ tree
            .
            └── provisioning
                ├── host_vars
                │   └── remote
                ├── hosts.yml
                ├── roles
                │   └── setup
                │       ├── handlers
                │       │   └── main.yml
                │       └── tasks
                │           ├── docker.yml
                │           └── main.yml
                │           └── config.yml
                │           └── install.yml
                │           └── nvm&node.yml
                └── site.yml

 

## General information and terminology

#### The `hosts` file

You will need to put the IP address of each server in the `hosts` file. If you only plan to spin up 1 server then you can just use the same IP address for each group. Setting up a dynamic hosts file is out of scope and is well documented elsewhere.

#### The `site.yml` file

This is the playbook. It consists of 1 or more plays. A play is a series of tasks associated to a group of servers. The tasks themselves could be inside of roles. It is fairly common to see and say "A play has many roles and each role has many tasks".

#### The `inventory` directory

This is what I like to label as configuration data. Sensitive information may or may not be included here and may or may not be checked into version control. It's up to you. It is very beneficial to be able to use the same playbook for many different sites. Having your inventory isolated away from the playbook allows you to do this.

### Build

$ ansible-playbook provisioning/site.yml -i provisioning/hosts.yml
