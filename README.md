# Ansible LEMP Stack Deployment - DevOps Project

## Project Overview
This project automates the deployment and configuration of a LEMP (Linux, Nginx, MariaDB, PHP-FPM) stack using Ansible. It demonstrates Infrastructure as Code (IaC) principles and configuration management best practices.

## ✅ What We Achieved

### Infrastructure Setup
- ✅ **VirtualBox 7.2.4** installed and configured
- ✅ **Vagrant 2.4.9** installed and working
- ✅ **2 Ubuntu 20.04 VMs** provisioned:
  - web01 (192.168.56.10) - Web server
  - db01 (192.168.56.11) - Database server
- ✅ **VM Networking** configured (private network 192.168.56.x)
- ✅ **SSH Access** working between host and VMs

### Ansible Configuration
- ✅ **Project Structure** following Ansible best practices
- ✅ **Roles-based architecture** (common, webserver, database)
- ✅ **Inventory management** with group_vars and host_vars
- ✅ **Playbooks** for orchestration
- ✅ **Idempotent configurations** implemented

## 🛠️ Technical Architecture
Host Machine (Windows + Git Bash)
│
├── Vagrant (VM Management)
│ ├── web01 (Ubuntu 20.04) - Nginx + PHP-FPM
│ └── db01 (Ubuntu 20.04) - MariaDB
│
└── Ansible (Configuration Management)
├── Roles (common, webserver, database)
├── Playbooks (site.yml)
└── Variables (group_vars, host_vars)

## 📁 Project Structure
ansible-lemp-stack/
├── Vagrantfile # VM definitions and network config
├── ansible.cfg # Ansible configuration
├── inventory/hosts.ini # Inventory with web01 and db01
├── playbooks/site.yml # Main orchestration playbook
├── group_vars/ # Group-specific variables
│ ├── all.yml # Common variables
│ ├── webservers.yml # Web server variables
│ └── databases.yml # Database variables
├── host_vars/ # Host-specific variables
└── roles/ # Ansible roles
├── common/ # Common server setup
│ ├── tasks/main.yml # Update, firewall, packages
│ ├── handlers/main.yml # Service handlers
│ └── vars/main.yml # Role variables
├── webserver/ # Nginx + PHP role
│ ├── tasks/main.yml # Install/config Nginx+PHP
│ ├── handlers/main.yml # Service handlers
│ ├── templates/nginx.conf.j2 # Nginx template
│ └── vars/main.yml # Web server variables
└── database/ # MariaDB role
├── tasks/main.yml # Install/config MariaDB
├── handlers/main.yml # Service handlers
├── templates/my.cnf.j2 # DB config template
└── vars/main.yml # Database variables

## 🔧 Prerequisites Installed
- VirtualBox 7.2.4
- Vagrant 2.4.9
- Git for Windows
- Python 3.13 (with Ansible compatibility notes)

## 🚦 How to Run (Linux/macOS or Windows with WSL/Docker)

### Step 1: Clone Repository
git clone https://github.com/Kartik27baliyan/ansible-lemp-stack.git
cd ansible-lemp-stack
Step 2: Start Virtual Machines
vagrant up
# Creates 2 VMs: web01 (192.168.56.10) and db01 (192.168.56.11)
Step 3: Run Ansible Playbook
Option A: Using Docker (Windows compatible)
docker run --rm -it \\
  -v $(pwd):/ansible \\
  -w /ansible \\
  williamyeh/ansible:alpine3 \\
  ansible-playbook playbooks/site.yml
Option B: Using WSL (Recommended for Windows)
# In WSL Ubuntu terminal
sudo apt update
sudo apt install ansible
ansible-playbook playbooks/site.yml
Option C: Linux/macOS Native
ansible-playbook playbooks/site.yml
Step 4: Verify Deployment
# Test web server
curl http://192.168.56.10
# Should show PHP info page
⚠️ Challenges & Solutions
Challenge 1: Ansible on Windows with Python 3.13
Issue: OSError: [WinError 1] Incorrect function due to blocking I/O changes in Python 3.13
Solution: Use WSL, Docker, or set ANSIBLE_NO_BLOCKING_IO=1 environment variable

Challenge 2: Vagrant vbguest Plugin
Issue: Unknown configuration section 'vbguest'
Solution: Removed plugin configuration (optional component)

Challenge 3: Terminal Input Issues in VMs
Issue: Input problems in VirtualBox terminal
Solution: Use SSH from host or Docker containers for execution

🎯 Learning Outcomes
Infrastructure as Code: Automated VM provisioning with Vagrant

Configuration Management: Idempotent server configuration with Ansible

Role-Based Architecture: Modular, reusable Ansible roles

Inventory Management: Dynamic inventory with variables

Troubleshooting: Real-world problem-solving with DevOps tools

Documentation: Comprehensive project documentation

📈 Skills Demonstrated

✅ Vagrant VM management

✅ Ansible playbook development

✅ Role-based configuration

✅ YAML configuration files

✅ SSH key management

✅ Network configuration

✅ Problem-solving and debugging

✅ Project documentation

🔄 Future Enhancements

Add Ansible Vault for secure credentials

Implement CI/CD pipeline (GitHub Actions)

Add monitoring (Prometheus + Grafana)

Containerize with Docker

Multi-environment deployment (dev/stage/prod)

📝 Notes for Windows Users
This project was developed on Windows with:
Git Bash for terminal

VirtualBox for virtualization

Vagrant for VM management

WSL/Docker recommended for Ansible execution

👨‍💻 Author
Kartik Baliyan

GitHub: @Kartik27baliyan
Project: Ansible LEMP Stack
📄 License
MIT License - Feel free to use this project for learning and portfolio purposes.
