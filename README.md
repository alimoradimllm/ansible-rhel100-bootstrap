# ansible-rhel100-bootstrap
rhel-vm-setup

This repository provides an Ansible playbook to automate the initial setup and security hardening of **100+ RHEL-based virtual machines**. It is designed for system administrators managing large-scale Linux environments who want fast, consistent, and secure baseline configuration.

---

## ✨ Features

The playbook performs the following actions on all target VMs:

- ✅ Creates a privileged user `admin-ali`
- 🔑 Installs an SSH public key for secure login
- 🔐 Disables root login and password authentication over SSH
- 📦 Installs essential tools:
  - `nano`, `nload`, `screen`, `vim`, `htop`, `tmux`, `wget`, `net-tools`, `git`
- 🌐 Configures timezone to `Asia/Tehran`
- ⏱ Enables and starts NTP service (`chronyd`)
- 🔥 Enables and starts `firewalld`
- 🔁 Optional reboot if multiple kernel versions detected (tagged)

---

## 📁 Directory Structure
ansible-rhel100-bootstrap/

├── site.yml 

├── inventory/
 └── hosts 

├── group_vars/
 └── all.yml 

├── files/
 └── id_rsa.pub 

└── README.md
---
## 🚀 Getting Started

### 1. Clone the Repository


git clone https://github.com/your-username/ansible-rhel100-bootstrap.git

cd ansible-rhel100-bootstrap

---
2. Edit Inventory (inventory/hosts):


[all]

vm01 ansible_host=192.168.1.1

vm02 ansible_host=192.168.1.2

...
vm100 ansible_host=192.168.1.100

---
3. Set Password Variable (group_vars/all.yml):


admin_ali_password: "YourSecurePasswordHere"

This will be SHA‑512 hashed automatically.

---
4. Add SSH Key (files/id_rsa.pub):

   
Your public key, e.g.:

ssh-rsa AAAAB3... your_email@example.com

---
5. Run the playbook:

ansible-playbook -i inventory/hosts site.yml

---

🔐 Security Notes
Root SSH login is disabled

SSH password authentication is disabled (key-only mode)

admin-ali has sudo access via wheel group

SSH key-based access is enforced

📋 Requirements
Ansible ≥ 2.9

Passwordless SSH from control node (or use --ask-pass for initial connection)

RHEL-compatible OS (RHEL, Rocky, AlmaLinux, etc.)

🚧 Customization Tips
Add more packages by editing the yum task

Change timezone or NTP servers via variables

Extend playbook with roles for Docker, monitoring, etc.

Use --limit to apply changes to specific hosts/groups


### 🔧 Fixes Made:
- Wrapped the directory structure in a proper fenced code block (` ``` `)
- Fixed indentation issues under `inventory/`, `group_vars/`, etc.
- Removed stray lines like `yaml` and `Copy/Edit` which appear to be clipboard artifacts
- Ensured consistent Markdown formatting

📜 License
MIT License — feel free to use, modify, and contribute!
