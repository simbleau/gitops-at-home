<div align="center">

<img src="https://simpleicons.org/icons/ubuntu.svg" width="144px" height="144px"/>

# Ubuntu Workstation
[![ubuntu version](https://img.shields.io/badge/22.04-E95421?style=for-the-badge&logo=ubuntu&label=Ubuntu&logoColor=white)](https://releases.ubuntu.com/22.04/)
[![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)](https://ansible.com/)

</div>

---

## 📖 Overview
This directory contains [__Ansible__](https://ansible.com) playbooks and roles to provisioning my [__Ubuntu 22.04 Jammy Jellyfish__](https://releases.ubuntu.com/22.04/) workstation.

---

## 📁 Directories
- [__`inventory`__](./inventory/): Ansible hosts and environment variables.
- [__`playbooks`__](./playbooks/): Ansible playbooks and automation.
- [__`roles`__](./playbooks/): Ansible roles.

---

## 🏁 Provisioning Steps
### Dependencies
- [ ] Install [SOPS](https://github.com/mozilla/sops) for sensitive file decryption (**required**)
  > Releases: [https://github.com/mozilla/sops/releases](https://github.com/mozilla/sops/releases)
- [ ] Mount access to the SOPS `keys.txt`
- [ ] Set the file path of the SOPS keys:
  > `export SOPS_AGE_KEY_FILE="/mnt/../sops/age/keys.txt"`
- [ ] Install ansible
  > `sudo apt install ansible`
- [ ] Install ansible requirements
  > `ansible-galaxy install -r requirements.yml`

### Provision Desktop
- [ ] Run provisioning playbook
```ansible
ansible-playbook \
--connection=local \
--inventory 127.0.0.1, \
--limit 127.0.0.1 \
./playbooks/provision.yml
```
