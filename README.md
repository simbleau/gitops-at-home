<div align="center">

<img src="https://simpleicons.org/icons/homeassistant.svg" width="144px" height="144px"/>

# Home Ops
[![sponsor me](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white)](https://github.com/sponsors/simbleau)
[![buy me a coffee](https://img.shields.io/badge/Buy_Me_A_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/simbleau)

[![internet](https://img.shields.io/uptimerobot/status/m791626909-5410cf23ca18cabcf74e32fa?color=lightgray&label=my%20home%20internet&style=flat-square&logo=opnSense&logoColor=white)](https://uptimerobot.com)
[![website](https://img.shields.io/uptimerobot/status/m791626907-5129386a08c0539012946152?logo=googlechrome&logoColor=white&color=lightgray&label=my%20website&style=flat-square)](https://spencer.imbleau.com)
[![home assistant](https://img.shields.io/uptimerobot/status/m791626943-e78c1a531a0ebfe443491da8?logo=homeassistant&logoColor=white&color=lightgray&label=my%20home%20assistant&style=flat-square)](https://www.home-assistant.io/)

</div>

---

## 📖 Overview
This is a mono repository for my home infrastructure and Kubernetes cluster. I try to adhere to Infrastructure as Code (IaC) and GitOps practices using tools like [__Ansible__](https://www.ansible.com/), [__Terraform__](https://www.terraform.io/), [__Kubernetes__](https://kubernetes.io/), [__Flux__](https://fluxcd.io/), [__Renovate__](https://renovatebot.com/) and [__GitHub Actions__](https://github.com/features/actions). Secrets are protected with modern [__Age__](https://github.com/FiloSottile/age) encryption.

### 💰 _Every tool used is open source or used freely._

---

## 📁 Directories

- [__`k8s`__](./k8s/): directory contains my Kubernetes configuration and artifacts.
- [__`provision`__](./provision/): directory contains my Ansible playbooks and roles for provisioning my home infrastructure.

---

## ⛵ Kubernetes
I run a fully conformant Kubernetes cluster at home with K3S, provisioned overtop bare-metal Ubuntu 22.04 using Ansible. This is a semi hyperconverged cluster (HCI), with workloads and block storage sharing the same available resources from a centralized RAID 5 samba share.

📘 _[__Click here__](./k8s/README.md) to learn more about my cluster._

---

## 🏁 Provisioning
Currently, I automate the provisioning of the following systems at home:
- [__My Ubuntu workstation__](./provision/ubuntu-workstation/)
- [__My Kubernetes cluster__](./provision/k8s/)

📙 _[__Click here__](./provision/README.md) to see my Ansible playbooks and roles for provisioning my home infrastructure._

---

## 🌐 DNS
Over WAN, I have forwarded ports `80` and `443` from my router. I use [Cloudflare](https://www.cloudflare.com/) as a proxy to hide my home WAN IP and to firewall certain traffic, [external-dns](https://github.com/kubernetes-sigs/external-dns) as my external DNS, and [k8s_gateway](https://github.com/ori-edge/k8s_gateway) as my internal DNS.

📗 _[__Click here__](./k8s/README.md#-dns) to see how DNS is handled by my cluster._

---

## 🤖 GitOps
- [__Flux__](https://fluxcd.io/) watches my [`cluster`](./k8s/cluster/) folder and makes the changes to my cluster automatically, based on the YAML manifests.
- [__Renovate__](https://renovatebot.com/) watches the repository for dependency updates, and automatically generates PRs for them. Automerging is allowed.
- [__GitHub Actions__](https://github.com/features/actions) validates and tests push and merge requests for conflicts.
- [__GitHub Pages__](https://pages.github.com/) automatic deployment enables my repository to act as a Helm registry.

---

## 🔧 Hardware
| Device                      | Amt | OS Disk | Data Disk    | RAM   | OS           | Purpose             |
| --------------------------- | --- | ------- | ------------ | ----- | ------------ | ------------------- |
| ARRIS Surfboard SB6183      | 1   | N/A     | N/A          | 256MB | N/A          | Modem               |
| ASUS RT-AC68U               | 1   | N/A     | N/A          | 16GB  | ASUSWRT      | Router, oVPN, SMB   |
| Raspberry Pi 4B 2GB         | 1   | 32GB SD | N/A          | 2GB   | Ubuntu 22.04 | Kubernetes Master   |
| Raspberry Pi 4B 2GB         | 3   | 32GB SD | N/A          | 2GB   | Ubuntu 22.04 | Kubernetes Worker   |
| Raspberry Pi 3 Model B+     | 1   | 32GB SD | N/A          | 1GB   | Ubuntu 22.04 | Kubernetes Worker   |
| AC Infinity CLOUDPLATE T1-N | 1   | N/A     | N/A          | N/A   | Ubuntu 22.04 | Air Cooling         |
| Kingston SATA 3 2.5" SSD    | 4   | N/A     | 240 GB       | N/A   | N/A          | SATA 3 Internal SSD |
| QNAP TR-004 4 Bay DAS       | 1   | N/A     | 720 GB RAID5 | N/A   | N/A          | RAID 5 DAS          |
| ADJ Products PC-100A PDU    | 1   | N/A     | N/A          | N/A   | N/A          | PDU                 |

---

## 🔏 License
This project is dual-licensed under both [Apache 2.0](LICENSE-APACHE) and [MIT](LICENSE-MIT) licenses.
