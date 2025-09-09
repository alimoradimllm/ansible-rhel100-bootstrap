# Ansible RHEL Bootstrap

Ansible role/playbook to bootstrap and harden large fleets of RHEL, Rocky, or AlmaLinux servers (100+). It creates a privileged user with SSH keys, configures system security, installs base packages, and sets up time, firewall, and system services.

---

## Features

- Create a secure admin user with SSH key authentication  
- Configure `sshd` (disable root login, disable password auth, configurable options)  
- Install base packages via `ansible.builtin.package`  
- Configure system timezone (`ansible.posix.timezone`)  
- Set up chrony with custom NTP pools  
- Enable and configure firewalld with variable-defined services  
- Secure password hashing (`password_hash('sha512')`)  
- OS checks to ensure RedHat-family compliance  
- Scales to 100+ hosts with `serial` and `forks` control  

---

## Requirements

- Ansible 2.15+  
- Supported platforms: RHEL 8/9, Rocky Linux 8/9, AlmaLinux 8/9  
- SSH access with a privileged user (or root for first run)  

---

## Usage

Clone repo and run playbook:

```bash
git clone https://github.com/alimoradimllm/ansible-rhel100-bootstrap.git
cd ansible-rhel100-bootstrap
ansible-playbook -i inventory bootstrap.yml
```

Run for specific host/group:

```bash
ansible-playbook -i inventory bootstrap.yml --limit webservers
```

Use tags for partial runs:

```bash
ansible-playbook -i inventory bootstrap.yml --tags "sshd,packages"
```

---

## Variables

Define in `group_vars/all.yml` or host-specific vars:

```yaml
admin_user: "ansibleadmin"
admin_ssh_key: "~/.ssh/id_rsa.pub"
sshd_disable_root: true
sshd_password_auth: false
bootstrap_packages:
  - vim
  - curl
  - wget
firewalld_services:
  - ssh
  - http
timezone: "Asia/Tehran"
chrony_pools:
  - pool.ntp.org
```

---

## Inventory Example

```ini
[all]
server1 ansible_host=192.0.2.10
server2 ansible_host=192.0.2.11

[webservers]
server1

[dbservers]
server2
```

---

## Development & Testing

- Lint with [ansible-lint](https://ansible-lint.readthedocs.io/)  
- Test with [Molecule](https://molecule.readthedocs.io/) and Docker images (`rockylinux:9`, `almalinux:9`)  
- Use `requirements.yml` for collections  

---

## Security Notes

- Use [Ansible Vault](https://docs.ansible.com/ansible/latest/vault_guide/index.html) for secrets  
- Do not commit real SSH keys or passwords into the repo  

---

## License

[MIT](LICENSE)

---

## Changelog

- **v1.0.0** – Initial bootstrap playbook  
- **v1.1.0** – Converted into role structure, added vars/handlers, Molecule tests  
