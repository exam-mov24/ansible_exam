# ansible_exam
## Final project for the MOV24 course

This project will be about ansible and how it works.
Setup in this project will be 
1 Manager vm. Ubuntu OS desktop version. From here ansible will manage other hosts
1 Ubuntu 24.04 server
2 Debian 13 server

1 Ubuntu server will be a web-server
1 debian will handle docker and application like IT-Tools
1 debian will become an SQL DB







Ansible is an agentless automation tool that you install on a single host.
Example is that you install it on you desktop or a dedicated server for it and it can be installed simply with very few commands or step.
For Ubuntu all that is needed for it to be installed is running command to update packaged first and than running the install command:
```bash
# update packade manager
apt update

# install ansible
apt install ansible
```
More ways to install ansible:
[ansible installation guide](https://docs.ansible.com/projects/ansible/latest/installation_guide/intro_installation.html#managed-node-requirements)

Thats it its now installed

Ansible uses SSH for connection and to manage hosts. No agents needs to be installed.
Its just important to know that the host has ssh enabled and that ansible has the passwrod or ssh-key for the host.
My way to run this is to have ready template to create/install my hosts.
Example is that Debian and Ubuntu are installed with a template on this example, proxmox.
The temple kickstarts a virtuall machine with wanted OS, user name, ssh-key and so on. so these machine are empty but has all the needed credentials added. Easy and fast to get up and running for work tasks.


Ansible in writen in python codes. But for seting up playbook and etc (will be seen later in the README ) YAML code is used.
templates and variables are connected/written in jinja2.
when ansible talks to a host/module it uses JSON.but that ansible handles all itself.
Powershell is also used when it comes to windows system









### Structure

This is the structure that will be setup

```bash
ansible_exam/
├── ansible.cfg
├── inventory
├── playbooks/
│   ├── site.yml
│   ├── web.yml
│   └── docker.yml
├── group_vars/
│   ├── all.yml          # vars for all hosts
│   ├── debian.yml       # vars for group [debian]
│   └── ubuntu.yml       # vars for group [ubuntu]
├── host_vars/
│   ├── debian1.yml
│   └── ubuntu1.yml
└── roles/
    ├── apache_php/
    │   ├── tasks/
    │   │   └── main.yml
    │   ├── templates/
    │   │   └── index.html.j2
    │   ├── files/
    │   ├── handlers/
    │   │   └── main.yml
    │   ├── vars/
    │   │   └── main.yml
    │   └── defaults/
    │       └── main.yml
    └── docker_host/
        └── tasks/
            └── main.yml
```