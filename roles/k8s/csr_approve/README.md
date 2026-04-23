# kubeadm masters init

Approve CSR per node in cluster. Role approve only per node( used `inventory_hostname`)

## Requirements

- Helm binary

- installed kubernetes pip package

## Usage

Run role on groups `k8s`

## Variables

| Name | type | default | description|
| --- | --- | --- | --- |
| `csr_approve_become` | string | `true` | Become method use |
| `csr_approve_kubeconfig` | string | "/etc/kubernetes/admin.conf" | Path to kubeconfig |
| `csr_approve_master_group` | string | "masters" | Group name of master |
