# Cilium

Install CNI cilium

## Requirements

- Helm binary

- installed kubernetes pip package

## Usage

Overwrite:

- `cilium_pod_subnet_cidr` - Pod subnet CIDR

## Variables

| Name                                  | type   | default                                      | description                                                                                                                |
|---------------------------------------|--------|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| `cilium_image_repo`                   | string | quay.io/cilium/cilium                        | Image repo for cilium/cilium                                                                                               |
| `cilium_image_tag`                    | string | v1.11.2                                      | Image tag for cilium/cilium                                                                                                |
| `cilium_operator_generic_image_repo`  | string | quay.io/cilium/operator-generic              | Image repo for cilium/operator-generic                                                                                     |
| `cilium_operator_generic_image_tag`   | string | v1.11.2                                      | Image tag for cilium/operator-generic                                                                                      |
| `cilium_hubble_relay_image_repo`      | string | quay.io/cilium/hubble-relay                  | Image repo for cilium/hubble-relay                                                                                         |
| `cilium_hubble_relay_image_tag`       | string | v1.11.2                                      | Image tag for cilium/hubble-relay                                                                                          |
| `cilium_hubble_ui_backend_image_repo` | string | quay.io/cilium/hubble-ui-backend             | Image repo for cilium/hubble-ui-backend                                                                                    |
| `cilium_hubble_ui_backend_image_tag`  | string | v0.8.5                                       | Image tag for cilium/hubble-ui-backend                                                                                     |
| `cilium_hubble_ui_image_repo`         | string | quay.io/cilium/hubble-ui                     | Image repo for cilium/hubble-ui                                                                                            |
| `cilium_hubble_ui_image_tag`          | string | v0.8.5                                       | Image tag for cilium/hubble-ui                                                                                             |
| `cilium_envoy_image_repo`             | string | docker.io/envoyproxy/envoy                   | Image repo for envoyproxy/envoy                                                                                            |
| `cilium_envoy_image_tag`              | string | v1.18.4                                      | Image tag for envoyproxy/envoy                                                                                             |
| `cilium_hubble_relay_node_selector`   | string | { node-role.kubernetes.io/worker: "" }       | Hubble deployment node-selector                                                                                            |
| `cilium_config_path`                  | string | /etc/kubernetes/cilium                       | Path, where stored helm values of cilium                                                                                   |
| `cilium_namespace`                    | string | cluster-cilium                               | Cilium namespace                                                                                                           |
| `cilium_helm_bin_path`                | string | "/usr/local/bin/helm"                        | Path, where place helm binary                                                                                              |
| `cilium_helm_repo_url`                | string | https://helm.cilium.io/                      | URL helm repo of cilium                                                                                                    |
| `cilium_helm_chart_version`           | string | 1.11.2                                       | Cilium helm chart version                                                                                                  |
| `cilium_pod_subnet_cidr`              | string | "192.168.0.0/16"                             | Pod subnet CIDR                                                                                                            |
| `cilium_hubble_enable`                | bool   | false                                        | Flag for add hubble deployment                                                                                             |
| `cilium_egressip_enabled`             | bool   | true                                         | Flag for add EgressIP feature                                                                                              |
| `cilium_monitoring_features`          | bool   | true                                         | Flag for add metrics ports                                                                                                 |
| `cilium_kubeproxy_replace`            | bool   | true                                         | Flag for remove kube-proxy daemonset                                                                                       |
| `cilium_tunnel_name`                  | string | geneve                                       | Cilium tunnel mode                                                                                                         |
| `cilium_cri_name`                     | string | containerd                                   | CRI name ( containerRuntime.integration )                                                                                  |
| `cilium_cri_socket_path`              | string | "/run/containerd/containerd.sock"            | Host path to CRI socket                                                                                                    |
| `cilium_hubble_external_hostname`     | string | hubble.apps.localhost                        | Ingress host of hubble                                                                                                     |
| `cilium_kubeconfig`                   | string | /etc/kubernetes/admin.conf                   | kubeconfig path on host                                                                                                    |
| `cilium_helm_force`                   | bool   | false                                        | Force run `helm upgrade` handler                                                                                           |
| `cilium_k8s_api_host`                 | string | "api.{{ cluster_name }}.{{ domain_suffix }}" | Hostname kubernetes api                                                                                                    |
| `cilium_k8s_api_port`                 | int    | 6443                                         | Port of kubernetes api                                                                                                     |
| `cilium_hubble_enabled`               | bool   | false                                        | Включить/выключить хаббл                                                                                                   |
| `cilium_deploy_with_features`         | bool   | false                                        | Флаг, переключающий роль в режим развёртывания с расширенным функционалом, который нельзя запустить при бутстрапе кластера |
| `cillium_use_itcacmcpl` | bool | {{ cluster_use_itcacmcpl | default(false) }} | Флаг, который заставляет роль получать сертификаты через ЕСАУС ЦУГИ |
| `cillium_itcacmcpl_cert_duration` | string | {{ cluster_itcacmcpl_cert_duration | default('8760h') }} | Параметр для AutoCertificate, при достижении 40% от этой длительности оператор попытается обновить сертификат  |
| `cilium_cli_path` | string | /app/cilium | Адрес, куда будет разахивирован cilium cli  |
| `cilium_cli_url`| string | https://github.com/cilium/cilium-cli/releases/download/v0.12.3/ | адрес для загрузки клиента cilium  |
| `hubble_cli_url` | string | https://github.com/cilium/hubble/releases/download/v0.10.0/ | адрес для загрузки клиента cilium  |
| `cilium_cli_url_headers` | string | {} | Хэдер для авторизации на S3 облачного портала, формируется из переменной distrib_store_token |
| `cilium_cli_url_headers` | string | "" | Адрес прокси для загрузки бинаря |
