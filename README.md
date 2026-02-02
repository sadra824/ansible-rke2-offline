ansible-rke2-offline

Deploy an offline RKE2 Kubernetes cluster on remote hosts using Ansible from a client machine.

Prerequisites

Ansible installed on the client machine

SSH access to target hosts

sudo privileges on all nodes

Internet access only on the client (for initial file download)

Download Required RKE2 Files

Download the following files on the client machine:

    curl -LO https://github.com/rancher/rke2/releases/download/v1.34.3%2Brke2r1/rke2.linux-amd64.tar.gz

    curl -LO https://github.com/rancher/rke2/releases/download/v1.34.3+rke2r1/rke2-images.linux-amd64.tar.zst

File Placement

Place the downloaded files in the following directory:

ansible-rke2-offline/
└── roles/
    └── rke2-server/
        ├── rke2.linux-amd64.tar.gz
        └── rke2-images.linux-amd64.tar.zst

Run the Playbook

After configuring the inventory and variables, run the playbook:

    ansible-playbook -i inventory/hosts.ini site.yml --ask-become-pass

Notes

This playbook is designed for air-gapped / offline environments.

RKE2 binaries and Kubernetes images are loaded from local files.

Target nodes do not require internet access.

The main installation and configuration logic is implemented in the rke2-server role.
