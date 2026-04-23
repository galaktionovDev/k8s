# kubernetes metrics helm installer

Роль для установки различных RB и всего что связано с ролевой моделью
## Requirements

Роль ожидает, что:

* kubernetes api запущено и работает
* на узлах из группы masters установлена библиотеки python для работы kubernetes.core
* на узлах из группы masters по адресу /etc/kubernetes/admin.conf или в том что определён как cluster_kubeconfig  есть kubeconfig с необходимимы правами


## Role Variables

| Variable                           | Required | Default                           | Type                           | Comments                                                                                         |
| ---------------------------------- | -------- | --------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------ |
| `kube_metrics_enabled`             | yes      | false                             | String                         | Установить kube metrics                                                                          |
| `kube_metrics_config_path`         | no       | /etc/kubernetes/templates         | String                         | Путь к папке, где будет сгенерирован конфиг                                                      |
| `kube_metrics_kubeconfig`          | no       | cluster_kubeconfig                | default                        | String                                                                                           | Адрес кубконфига |
| `kube_metrics_update_rules_only`   | no       | false                             | Bool                           | Меняет логику работы, пропускает шаг установки и только обновляет правила                        |
| `kube_metrics_name`                | no       | kube-metrics                      | String                         | Имя релиза Helm                                                                                  |
| `kube_metrics_helm_force`          | no       | false                             | Bool                           | Меняет логику работы, роль будет пытаться обновить релиз helm, без условий                       |
| `kube_metrics_helm_bin_path`       | no       | cluster_helm_bin                  | default('/usr/local/bin/helm') | Путь к бинарю helm                                                                               |
| `kube_metrics_helm_chart_name`     | no       | metrics-server                    | String                         | Имя чарта                                                                                        |
| `kube_metrics_helm_repo`       | no       | cluster_helm_repo                      | String                         | Имя репы с чартами и логопассом, если cluster_helm_repo не определён, то установка упадет |
| `kube_metrics_helm_chart_version`  | no       | 3.8.2                             | String                         | Версия чарта с метриками                                                                         |
| `kube_metrics_helm_debug`          | no       | false                             | Bool                           | Отключить атомарную установку helm                                                               |
| `kube_metrics_namespace`           | no       | cluster-kube-metrics              | String                         | Неймспейс, который будет создан и в него установлено приложение метрик                           |
| `kube_metrics_registry`            | no       | k8s.gcr.io/metrics-server         | String                         | Регистри образа метрик                                                                           |
| `kube_metrics_image_name`          | no       | metrics-server/metrics-server     | String                         | Имя образа                                                                                       |
| `kube_metrics_image_tag`           | no       | v0.6.2                            | String                         | Тэг образа                                                                                       |
| `kube_metrics_pullpolicy`          | no       | IfNotPresent                      | String                         | Политика загрузки образов                                                                        |
| `kube_metrics_replicas`            | no       | 2                                 | String                         | Количество реплик в деплойменте                                                                  |
| `kube_metrics_maxsurge`            | no       | 0                                 | String                         | maxSurge в deployment                                                                            |
| `kube_metrics_maxunavailable`      | no       | 1                                 | String                         | kube_metrics_maxUnavailable в deployment                                                         |
| `kube_metrics_pdb_enabled`         | no       | true                              | Bool                           | Создавать pdb для сервиса                                                                        |
| `kube_metrics_pdb_min_available`   | no       | 1                                 | String                         | Минимальное число реплик в pdb                                                                   |
| `kube_metrics_args`                | no       | --kubelet-insecure-tls            | list                           | Список доп аргументов к подам                                                                    |
| `kube_metrics_own_metrics_enabled` | no       | monitoring_enabled                | default(false)                 | Если мониторинг включен, создаёт servicemonitor                                                  |
| `kube_metrics_psp_enabled`         | no       | false                             | Bool                           | Включить создание политик psp                                                                    |
| `kube_metrics_resource_req_cpu`    | no       | 100m                              | String                         | Реквест по процессору для подов                                                                  |
| `kube_metrics_resource_req_memory` | no       | 300Mi                             | String                         | Реквест по памяти для подов                                                                      |
| `kube_metrics_nodeselector`        | no       | node-role.kubernetes.io/infra: "" | Dict                           | Селектор нод для подов метрик                                                                    |


## Global variables:

| Role variable              | Global Variable            |
| -------------------------- | -------------------------- |
| kube_metrics_kubeconfig    | cluster_kubeconfig         |
| kube_metrics_helm_bin_path | cluster_helm_bin           |
| kube_metrics_helm_repo     | cluster_helm_repo |


Example Playbook
----------------

    - hosts: masters
      roles:
        - k8s_features/kubernetes_metrics
      vars:
        kube_metrics_enabled: true
    
      
## Author Information
EG
