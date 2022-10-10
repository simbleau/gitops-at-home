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
- [ ] Decrypt inventory files
  > `sops -d ./inventory/inventory.sops.yml > ./inventory/inventory.yml`
- [ ] Install ansible
  > `sudo apt install ansible`
- [ ] Install ansible requirements
  > `ansible-galaxy install -r requirements.yml`


### Prepare
Kubernetes requires system-specific changes to memory, cpu, scheduling, etc. The preparation playbook will make the required changes and reboot the system.
- [ ] Run preparation
  - [ ] Optional: add `--limit` with arguments (e.g. groups `master`, `worker`, or nodes `worker-1`)
```ansible
ansible-playbook \
--user=ubuntu \
--ask-become-pass \
./playbooks/prepare.yml
```

### Installing cluster
- [ ] Run installation
  - [ ] Optional: add `--limit` with arguments (e.g. groups `master`, `worker`, or nodes `worker-1`)
```ansible
ansible-playbook \
--user=ubuntu \
--ask-become-pass \
./playbooks/install.yml
```

### Restart cluster
- [ ] Run playbook
  - [ ] Optional: add `--limit` with arguments (e.g. groups `master`, `worker`, or nodes `worker-1`)
```ansible
ansible-playbook \
--user=ubuntu \
--ask-become-pass \
./playbooks/restart.yml
```

### Reboot cluster
- [ ] Run playbook
  - [ ] Optional: add `--limit` with arguments (e.g. groups `master`, `worker`, or nodes `worker-1`)
```ansible
ansible-playbook \
--user=ubuntu \
--ask-become-pass \
./playbooks/reboot.yml
```

### Nuke cluster
⚠️ **This will destroy the Kubernetes cluster and remove all artifacts**.
- [ ] Run playbook
```ansible
ansible-playbook \
--user=ubuntu \
--ask-become-pass \
./playbooks/nuke.yml
```