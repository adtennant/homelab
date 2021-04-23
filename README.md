# homelab

Monorepo for my homelab.

## Prerequisites

- ansible
- sshpass
- sops

## Getting Started

- Flash Pis with Rasberian Lite
- Grant Pis static IPs (done in router settings based on MAC address so they persist between flashes)
- ansible-playbook ansible/site.yml --ask-pass -i ansible/cluster --extra-vars "gpg_secret_key='$(gpg --export-secret-keys --armor "37C23DD5B51CB2EC4563E984F73FEEB5DD741796")'"
- scp pi@192.168.50.200:~/.kube/config ~/.kube/homelab
- Profit

## Features/Goals

- Hardware Setup
  - [x] Static IPs (configured in router settings based on MAC address so they persist between flashes)
  - [x] Single command to go from flashed Raspberry Pi's to a bootstrapped cluster (`ansible`)
- Node Maintenance
  - [x] Automated package security updates
  - [x] Docker image pruning
  - [x] Log rotation
  - [x] Log pruning
  - [x] Temp file pruning
- Kubernetes
  - [x] Automated deployments using FluxCD
  - [x] Git-safe secrets management using `sops`.
  - `cert-manager`
    - [x] Automated TLS certificates
    - [x] DNS01 challenges via Cloudflare
  - `external-dns`
    - [x] Automated Cloudflare DNS updates
  - `grafana`
    - TBD
  - `longhorn`
    - TBD
  - `metallb`
    - [x] `LoadBalancer` services using Layer2 mode.
  - `monitoring`
    - [x] `prometheus-operator`
    - [x] `speedtest-prometheus`
    - TBD
  - `system-upgrade-controller`
    - [x] Automated updates on the `stable` channel
  - `traefik`
    - [x] Routing using Ingress manifests
    - [x] Expose the `traefik` dashboard without using an `IngressRoute`
