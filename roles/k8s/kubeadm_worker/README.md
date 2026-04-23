# kubeadm workers

Append worker node to cluster

## Requirements

Role require:

- configured kubernetes apt repository

- installed kubelet, kubeadm

## Usage

Overwrite:

- `kubeadm_worker_k8s_version` - must be equal to whole cluster version

- `kubeadm_worker_cluster_api_hostname` - load balanced address of cluster api(without port)

- `kubeadm_worker_master_group` - groups name of kube-masters, where will be generate bootrap token

## Variables

| Name                                  | type   | default                                      | description                             |
| ------------------------------------- | ------ | -------------------------------------------- | --------------------------------------- |
| `kubeadm_worker_cluster_api_hostname` | string | "api.{{ cluster_name }}.{{ domain_suffix }}" | load balanced api hostname without port |
| `kubeadm_worker_cri_socket`           | string | "/var/run/containerd/containerd.sock"        | Path to CRI socket                      |
| `kubeadm_worker_k8s_version`          | string | : "v1.22.7"                                  | Version of k8s                          |
| `kubeadm_worker_cluster_name`         | string | : "{{ cluster_name }}"                       | Cluster name                            |
| `kubeadm_worker_service_cidr`         | string | : "10.96.0.0/12"                             | CIDR of service network                 |
| `kubeadm_worker_pod_network_cidr`     | string | : "10.124.0.0/16"                            | CIDR of pod network                     |
| `kubeadm_worker_master_group`         | string | masters                                      | Ansible Group name with only masters    |
| `kubeadm_worker_no_log`               | bool   | false                                        | Flag to `no_log`                        |
| `kubeadm_worker_become` | bool | true | Flag to `become` |
| `kubeadm_worker_kubeconfig` | string | /etc/kubernetes/admin.conf | Path ot kubeconfig on controller node |
