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
│ └── hosts 
├── group_vars/
│ └── all.yml 
├── files/
│ └── id_rsa.pub 
└── README.md
---
## 🚀 Getting Started

### 1. Clone the Repository


git clone https://github.com/your-username/ansible-rhel100-bootstrap.git
cd ansible-rhel100-bootstrap

---

### 🔧 Fixes Made:
- Wrapped the directory structure in a proper fenced code block (` ``` `)
- Fixed indentation issues under `inventory/`, `group_vars/`, etc.
- Removed stray lines like `yaml` and `Copy/Edit` which appear to be clipboard artifacts
- Ensured consistent Markdown formatting

