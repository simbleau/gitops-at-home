<div align="center">

<img src="https://simpleicons.org/icons/linux.svg" width="144px" height="144px"/>

# NFS Server
[![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)](https://ansible.com/)

</div>

---

## 📖 Overview
This directory contains [__Ansible__](https://ansible.com) playbooks and roles to provisioning my [__nfs__](https://www.geeksforgeeks.org/network-file-system-nfs/) servers and clients.

---

## 📁 Directories
- [__`inventory`__](./inventory/): Ansible hosts and environment variables.
- [__`playbooks`__](./playbooks/): Ansible playbooks and automation.

---

## 🏁 Provisioning Steps
### Dependencies
- [ ] Install [SOPS](https://github.com/mozilla/sops) for sensitive file decryption (**required**)
  > Releases: [https://github.com/mozilla/sops/releases](https://github.com/mozilla/sops/releases)
- [ ] Mount access to the SOPS `keys.txt`
- [ ] Set the file path of the SOPS keys:
  > `export SOPS_AGE_KEY_FILE="/mnt/../sops/age/keys.txt"`
- [ ] Decrypt inventory files
  > `sops -d ./inventory/inventory.sops.yml > ./inventory/inventory.yml`
- [ ] Install ansible
  > `sudo apt install ansible`
- [ ] Install ansible requirements
  > `ansible-galaxy install -r requirements.yml`

### Installing servers
- [ ] Run installation
  - [ ] Optional: add `--limit` with arguments (e.g. groups `server`, `client`, or nodes `server-1`)
```ansible
ansible-playbook \
--user=ubuntu \
--ask-become-pass \
./playbooks/install_server.yml
```