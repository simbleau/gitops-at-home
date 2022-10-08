<div align="center">

<img src="https://simpleicons.org/icons/k3s.svg" width="144px" height="144px"/>

# K3S Cluster
[![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)](https://ansible.com/)

</div>

---

## 📖 Overview
This directory contains [__Ansible__](https://ansible.com) playbooks and roles to provisioning my [__K3S__](https://k3s.io/) cluster.

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

### Provisioning master nodes
- [ ] Set the username for initial connection (will be deleted)
  > `export ANSIBLE_REMOTE_USER='ubuntu'`
- [ ] Decrypt inventory file
  > `sops -d ./inventory/masters.sops.yml > ./inventory/masters.yml`
- [ ] Run provisioning playbook'
```ansible
ansible-playbook \
--inventory ./inventory/masters.yml \
./playbooks/provision_masters.yml
```

### Provisioning worker nodes
- [ ] Set the username for initial connection (will be deleted)
  > `export ANSIBLE_REMOTE_USER='ubuntu'`
- [ ] Decrypt inventory file
  > `sops -d ./inventory/workers.sops.yml > ./inventory/workers.yml`
- [ ] Run provisioning playbook'
  - [ ] Optional: add `--limit odd` or `--limit even` for half of the nodes
```ansible
ansible-playbook \
--inventory ./inventory/workers.yml \
./playbooks/provision_workers.yml
```

### Reboot cluster
- [ ] Set the username for initial connection (will be deleted)
  > `export ANSIBLE_REMOTE_USER='ubuntu'`
- [ ] Run provisioning playbook'
```ansible
ansible-playbook \
--inventory ./inventory/masters.yml \
--inventory ./inventory/workers.yml \
./playbooks/reboot.yml
```