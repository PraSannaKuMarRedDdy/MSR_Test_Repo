## MSR_COSMO Task

***What is ansible-playbooks?****

It is a set of [ansible](http://www.ansible.com/home) playbooks showing you how to create certain full server stacks.

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
                └── site.yml

 

