# Ansible LEMP Stack Deployment

## Project Overview
This project automates the deployment and configuration of a LEMP (Linux, Nginx, MariaDB, PHP-FPM) stack using Ansible. It demonstrates configuration management best practices including idempotent deployments, role-based organization, secure credential management, and infrastructure-as-code principles.

## ArchitectureControl Node (Your Machine) → Managed Nodes:

Web Server (web01): Nginx + PHP-FPM @ 192.168.56.10
Database Server (db01): MariaDB @ 192.168.56.11
## Prerequisites
- Ansible 2.9+
- VirtualBox 6.0+
- Vagrant 2.2+
- Git

## Windows Setup Instructions
1. Install Git for Windows (Git Bash)
2. Install VirtualBox from https://virtualbox.org
3. Install Vagrant from https://vagrantup.com
4. Install Ansible (see below)

### Installing Ansible on Windows
Option 1 (Recommended): Use Windows Subsystem for Linux (WSL)
```bash
# In Windows PowerShell (Admin)
wsl --install
# Then in WSL terminal:
sudo apt update
sudo apt install ansible
Option 2: Use Chocolatey
choco install ansible
##Project Structure
ansible-lemp-stack/
├── README.md
├── .gitignore
├── Vagrantfile
├── ansible.cfg
├── inventory/
│   └── hosts.ini
├── playbooks/
│   └── site.yml
├── group_vars/
│   ├── all.yml
│   ├── webservers.yml
│   └── databases.yml
├── host_vars/
└── roles/
    ├── common/
    │   └── tasks/
    │       └── main.yml
    ├── webserver/
    │   └── tasks/
    │       └── main.yml
    └── database/
        └── tasks/
            └── main.yml
'EOF'
