<div align="center">

<img src="https://simpleicons.org/icons/homeassistant.svg" width="144px" height="144px"/>

# Home Ops
</div>

---

## 📖 Overview
This is a mono repository for my home infrastructure and Kubernetes cluster. I try to adhere to Infrastructure as Code (IaC) and GitOps practices using tools like [__Ansible__](https://www.ansible.com/), [__Terraform__](https://www.terraform.io/), [__Kubernetes__](https://kubernetes.io/), [__Flux__](https://fluxcd.io/), [__Renovate__](https://renovatebot.com/) and [__GitHub Actions__](https://github.com/features/actions). Secrets are protected with modern [__Age__](https://github.com/FiloSottile/age) encryption.

### 💰 _Every tool used is open source or used freely._

---

## 📁 Directories

- [__`cluster`__](./cluster/): directory contains my Kubernetes configuration and artifacts, managed by Flux.
- [__`provision`__](./provision/): directory contains my Ansible playbooks and roles for provisioning my home infrastructure.

---

## ⛵ Kubernetes
I run a fully conformant Kubernetes cluster at home with K3S, provisioned overtop bare-metal Ubuntu 22.04 using Ansible. This is a semi hyperconverged cluster (HCI), with workloads and block storage sharing the same available resources from a centralized RAID 5 storage.

---

## 🏁 Provisioning
Currently, I automate the provisioning of the following systems at home:
- [__My Ubuntu workstation__](./provision/workstation/)
- [__My MacOS workstation__](./provision/workstation/)
- [__My K3S Kubernetes cluster__](./provision/k3s/)

📙 _[__Click here__](./provision/README.md) to see my Ansible playbooks and roles for provisioning my home infrastructure._

---

## 🌐 Dynamic DNS
Over WAN, I have forwarded ports `80` and `443` from my router. I use [Cloudflare](https://www.cloudflare.com/) as a proxy to hide my home WAN IP. I use [cddns](https://github.com/simbleau/cddns) as my Dynamic DNS.

---

## 🤖 GitOps
- [__Flux__](https://fluxcd.io/) watches my [`cluster`](./cluster/) folder and makes the changes to my cluster automatically, based on the YAML manifests.
- [__Renovate__](https://renovatebot.com/) watches the repository for dependency updates, and automatically generates PRs for them. Automerging is allowed.
- [__GitHub Actions__](https://github.com/features/actions) validates and tests push and merge requests for conflicts.

---

## 🔧 Hardware
| Device                      | Amt | OS Disk  | Data Disk    | RAM   | OS           | Purpose           |
| --------------------------- | --- | -------- | ------------ | ----- | ------------ | ----------------- |
| ARRIS Surfboard SB6183      | 1   | N/A      | N/A          | 256MB | N/A          | Modem             |
| Linksys AC1900              | 1   | N/A      | N/A          | 500MB | OpenWrt      | Router, DHCP      |
| HP ProDesk 600 G3 Mini      | 1   | 120GB SD | N/A          | 4GB   | Ubuntu 22.04 | Kubernetes Master |
| Raspberry Pi 4B 2GB         | 4   | 32GB  SD | N/A          | 2GB   | Ubuntu 22.04 | Kubernetes Worker |
| Raspberry Pi 3 Model B+     | 1   | 32GB  SD | N/A          | 1GB   | Ubuntu 22.04 | Kubernetes Worker |
| AC Infinity CLOUDPLATE T1-N | 1   | N/A      | N/A          | N/A   | N/A          | Air Cooling       |
| Kingston SATA 3 2.5" SSD    | 4   | N/A      | 240 GB       | N/A   | N/A          | SATA 3 SSD        |
| QNAP TR-004 4 Bay DAS       | 1   | N/A      | 720 GB RAID5 | N/A   | N/A          | RAID 5 DAS        |
| ADJ Products PC-100A PDU    | 1   | N/A      | N/A          | N/A   | N/A          | PDU               |

---

## 🔏 License
This project is dual-licensed under both [Apache 2.0](LICENSE-APACHE) and [MIT](LICENSE-MIT) licenses.
