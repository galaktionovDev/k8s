# Ingress

Deploys a Ingress controller ingress-nginx on a k8s cluster.

## Role Variables

| Variable                                   | Required | Default                                    | Type       | Comments                                                                                   |
| ------------------------------------------ | -------- | ------------------------------------------ | ---------- | ------------------------------------------------------------------------------------------ |
| `ingress_infra_enabled`                    | no       | true                                       | bool       | infra ingress would be installed if variable is defined                                    |
| `ingress_chart_name`                       | no       | ingress-nginx                              | string     | chart and container name                                                                   |
| `ingress_chart_version`                    | no       | 4.0.17                                     | string     | ingress helm chart version, default: latest                                                |
| `ingress_controller_image_repo`            | no       | k8s.gcr.io/ingress-nginx/controller        | string     | ingress controller container image repository                                              |
| `ingress_controller_image_tag`             | no       | v1.1.1                                     | string     | ingress controller container image tag                                                     |
| `ingress_namespace`                        | no       | cluster-ingress                            | string     | specifies namespace for deployment                                                         |
| `ingress_namespace_node_selector`          | no       | node-role.kubernetes.io/ingress=true       | string     | specifies node selector for namespace                                                      |
| `ingress_namespace_labels`                 | no       | networking.k8s.io/policy-group: ingress    | dictionary | specifies labels for namespace                                                             |
| `ingress_helm_force`                       | no       | false                                      | bool       | force run installation handler                                                             |
| `ingress_class`                            | no       | infra                                      | string     | specify ingressClass                                                                       |
| `ingress_group`                            | no       | ingress                                    | string     | inventory ingress group                                                                    |
| `ingress_replica_count`                    | no       | 0                                          | string     | specify replicaCount, count by `ingress_group` variable                                    | 
| `ingress_requests_memory`                  | no       | 125Mi                                      | string     | pod memory request                                                                         |
| `ingress_requests_cpu`                     | no       | 100m                                       | string     | pod cpu request                                                                            |
| `ingress_kind`                             | no       | Deployment                                 | string     | specify ingress kind, must be Deployment or DaemonSet                                      |
| `ingress_host_network`                     | no       | false                                      | bool       | specify --hostNetwork flag protocol                                                        |
| `ingress_proxy_protocol`                   | no       | false                                      | bool       | enables the Nginx PROXY protocol                                                           |
| `ingress_ssl_passthrough`                  | no       | false                                      | bool       | enables the SSL Passthrough feature                                                        |
| `ingress_shard_name`                       | no       | ""                                         | string     | specify nginx ingress class name (shard)                                                   |
| `ingress_group_name`                       | no       | ingress_{{ ingress_shard_name }}           | string     | specify ingress_shard_name                                                                 |
| `ingress_tcp_services`                     | no       | {}                                         | dictionary | specify TCP services                                                                       |
| `ingress_udp_services`                     | no       | {}                                         | dictionary | specify UDP services                                                                       |
| `ingress_kubeconfig`                       | no       | /etc/kubernetes/admin.conf                 | string     | kubeconfig path                                                                            |
| `ingress_helm_bin`                         | no       | /usr/local/bin/helm                        | string     | helm binary path                                                                           |
| `ingress_helm_hub_url`                     | no       | https://kubernetes.github.io/ingress-nginx | string     | ingress repository url                                                                     |
| `ingress_config_path`                      | no       | /etc/kubernetes/templates/ingress          | string     | directory with helm values                                                                 |
| `ingress_no_log`                           | no       | true                                       | bool       | Flag to `no_log` option                                                                    |
| `ingress_nginx_max_worker_connections`     | no       | 65536                                      | String     | Sets the maximum number of simultaneous connections that can be opened by each worker process |
| `ingress_nginx_disable_access_log`         | no       | true                                       | bool       | disables nginx acces log for perfomance reasons                                               |
| `drain_delete_node`                        | yes      | false                                      | bool       | flag for install OR delete shard                                                            | 

## Global variables:

| Role variable                  | Global Variable        |
| ------------------------------ | ---------------------- |
| `ingress_kubeconfig`           | `cluster_kubeconfig`   |
| `ingress_helm_bin`             | `cluster_helm_bin`     |
| `ingress_helm_hub_url`         | `helm_hub_url`         |
| `ingress_config_path`          | `cluster_config_path`  |
| `ingress_cert_manager_enabled` | `cert_manager_enabled` |
| `ingress_monitoring_enabled`   | `monitoring_enabled`   |
| `ingress_monitoring_name`      | `monitoring_name`      |
| `ingress_no_log`               | `cluster_no_log`       |

## Examples

| Variable                          | Example                              |
| --------------------------------- | ------------------------------------ |
| `ingress_tcp_services`            | 8080: "default/example-tcp-svc:9000" |
| `ingress_udp_services`            | 53: "kube-system/kube-dns:53"        |

## Author Information

EG
