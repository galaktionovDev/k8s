# kubeadm masters init

Init cluster on first master and joint other masters to cluster

## Requirements

Role require configured kubernetes apt repository

## Usage

Overwrite:

- `kubeadm_masters_init_k8s_version` - must be equal to whole cluster version

- `kubeadm_masters_init_cluster_api_hostname` - load balanced address of cluster api(without port)

## Variables

| Name                                        | type   | default                                           | description                             |
| ------------------------------------------- | ------ | ------------------------------------------------- | --------------------------------------- |
| `kubeadm_masters_init_cluster_name`         | string | "{{ cluster_name }}"                              | Cluster name                            |
| `kubeadm_masters_init_cluster_api_hostname` | string | "api.{{ cluster_name }}.{{ domain_suffix }}"      | load balanced api hostname without port |
| `kubeadm_masters_init_auth_fqdn`            | string | "auth.app.{{ cluster_name }}.{{ domain_suffix }}" | oidc issuer url                         |
| `kubeadm_masters_init_k8s_version`          | string | `v1.20.4`                                         | Version of cluster                      |
| `kubeadm_masters_init_cri_socket`           | string | "{{ cr_socket }}"                                 | Path to CRI socket                      |
| `kubeadm_masters_init_pod_network_cidr`     | string | `10.124.0.0/16`                                   | CIDR of pod network                     |
| `kubeadm_masters_init_service_cidr`         | string | `10.96.0.0/12`                                    | CIDR of pod network                     |
| `kubeadm_masters_init_etc_data_dir`         | string | `/app/etcd`                                       | path to etcd local directory            |
| `kubeadm_masters_init_token_ttl`            | string | 1h                                                | TTL of bootrap token                    |
| `kubeadm_masters_init_no_log`               | bool   | false                                             | Flag to `no_log`                        |
| `kubeadm_masters_init_vault_portal_url` | string | '' | Cloud Vault URL |
| `kubeadm_masters_init_vault_portal_role_id` | string | '' | Cloud Vault Role ID |
| `kubeadm_masters_init_vault_portal_secret_id` | string | '' | Cloud Vault Secret ID |
| `kubeadm_masters_init_vault_portal_path` | string | '' | Cloud Vault path in KV |
| `kubeadm_masters_init_vault_portal_kv` | string | '' | Cloud Vault KV name |
| `kubeadm_masters_init_kubeadm_tmp_dir` | string | /app/kubeadm-tmp | Path to directory for move kubeadm backup files |
| `kubeadm_masters_init_enabled_admission_plugins` | list | [NodeRestriction, PodNodeSelector] | List of admission plugins that will be enable |
| `kubeadm_matster_init_oidc_auth_enabled` | bool | false | Flag for use OIDC auth in cluster |
| `kubeadm_masters_init_etcd_extra_args_list` | dict | {snapshot-count: 100000, quota-backend-bytes: 7516192768} | Dict of etcd parameters that will be use |
| `kubeadm_masters_init_become` | bool | true | Flag for use `become` in tasks with `connection : local` |
| `kubeadm_masters_init_kubeconfig` | string | playbook_dir + '/cluster_config/' + cluster_name + '/cluster-kubeconfig.yaml' | Path to kbueconfig on controller node |
| `kubeadm_masters_init_audit_enabled` | bool | false | Flag to enable audit function on kube-apiserver |
| `kubeadm_masters_init_audit_version` | string | "v1.0.0" | Version of policy file |
| `kubeadm_masters_init_audit_config` | string | "/etc/kubernetes/audit-{{ kubeadm_masters_init_audit_version }}.yaml" | Path to policy file on remote host |
| `kubeadm_masters_init_audit_log_directory` | string | /var/log/kube-audit | Path for write audit logs from kube-apiserver |
| `kubeadm_masters_init_registry` | string | k8s.gcr.io | String for overwrite default registry hostname |
| `kubeadm_masters_init_masters_group_name` | string | masters | Group name with master nodes |
| `kubeadm_masters_init_coredns_nodeselectors` | dict | {node-role.kubernetes.io/master: "", kubernetes.io/os: linux} | Dict of nodeSelector for coreDNS |
