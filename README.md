
# Infra Configurações

Este repositório contém os scripts de provisionamento e configuração de ferramentas de infraestrutura utilizando **Ansible**. É voltado para ambientes em nuvem (como AWS) ou ambientes locais, e contempla componentes essenciais para clusters Kubernetes e ferramentas de apoio.

## 📁 Estrutura do Repositório

```
infra-configuracoes/
├── ansible.cfg                  # Arquivo de configuração do Ansible
├── inventory/                   # Inventários para ambientes (aws e local)
├── main.yml                     # Playbook principal para execução centralizada
│
├── bastion/                     # Configuração de host bastion (jump host)
│
├── kubernetes/                  # Instalação e configuração de cluster Kubernetes
│   └── instalação/
│       ├── roles/
│       │   ├── containerd-install/
│       │   ├── k8s-master/
│       │   ├── k8s-workers/
│       │   └── k8s-requirements/
│       └── configuration/       # Arquivos auxiliares (ex: cfg.yml)
│
├── grafana/                     # Provisionamento do Grafana com templates e configs
├── prometheus/                  # Configuração do Prometheus
├── haproxy/                     # Configuração do HAProxy para balanceamento
├── metallb/                     # Deploy e configuração do MetalLB
├── nfs-server/                  # Provisionamento de servidor NFS
```

## 🧰 Tecnologias Utilizadas

- [Ansible](https://www.ansible.com/)
- [Kubernetes](https://kubernetes.io/)
- [Prometheus](https://prometheus.io/)
- [Grafana](https://grafana.com/)
- [MetalLB](https://metallb.universe.tf/)
- [HAProxy](http://www.haproxy.org/)
- [NFS](https://nfs.sourceforge.net/)

## 🚀 Objetivo

Automatizar a configuração de ambientes de infraestrutura, com foco em:

- Clusters Kubernetes provisionados manualmente ou via EC2
- Monitoramento (Prometheus e Grafana)
- Load balancing (HAProxy, MetalLB)
- Armazenamento compartilhado (NFS)
- Acesso seguro via bastion host

## 📦 Inventários

O repositório possui dois arquivos de inventário:

- `inventory/aws/inv.yml` → Ambiente em nuvem
- `inventory/local/inv.yml` → Ambiente local

## 🔧 Execução

Para executar o playbook principal:

```bash
ansible-playbook -i inventory/aws/inv.yml main.yml
```

> Altere o inventário conforme o ambiente desejado (`aws` ou `local`).