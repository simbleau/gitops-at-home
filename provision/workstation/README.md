<div align="center">

<img src="https://simpleicons.org/icons/macos.svg" width="144px" height="144px"/>

# Workstation
[![ubuntu version](https://img.shields.io/badge/22.04-E95421?style=for-the-badge&logo=ubuntu&label=Ubuntu&logoColor=white)](https://releases.ubuntu.com/22.04/)
[![macOS version](https://img.shields.io/badge/Ventura%2013.0.1-E95421?style=for-the-badge&logo=macos&label=MacOS&logoColor=white)](https://releases.ubuntu.com/22.04/)

[![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)](https://ansible.com/)

</div>

---

## 📖 Overview
This directory contains [__Ansible__](https://ansible.com) playbooks and roles to provisioning my workstation for the following operating systems (detected at runtime):
- [__macOS Ventura__](https://www.apple.com/macos/ventura/)
- [__Ubuntu 22.04 Jammy Jellyfish__](https://releases.ubuntu.com/22.04/)

---

## 📁 Directories
- [__`inventory`__](./inventory/): Ansible hosts and environment variables.
- [__`playbooks`__](./playbooks/): Ansible playbooks and automation.
- [__`roles`__](./playbooks/): Ansible roles.

---

## 🏁 Provisioning Steps
### Dependencies
- [ ] Mount access to the SOPS `keys.txt`
- [ ] Set the file path of the SOPS keys:
  > `export SOPS_AGE_KEY_FILE="/mnt/../sops/age/keys.txt"`
- [ ] Install ansible
  - macOS
  > `python3 -m pip install --user ansible`
  - Ubuntu
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
