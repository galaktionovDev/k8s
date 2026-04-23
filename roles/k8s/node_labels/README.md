 node-labels

Append worker node to cluster

## Requirements

Роль ожидает, что:

* kubernetes api запущено и работает
* на узлах из группы masters установлена библиотеки python для работы kubernetes.core
* на узлах из группы masters по адресу /etc/kubernetes/admin.conf есть kubeconfig с необходимимы правами

## Usage

Задайте переменную node_labels в hostvars узлов в группе(по умолчанию группа k8s)

## Variables

| Name                         | Requared | type   | default | description                          |
| ---------------------------- | -------- | ------ | ------- | ------------------------------------ |
| `node_labels_masters_groups` | no       | String | masters | Переменная для списка хостов masters |
| `node_labels`                | no       | dict   | []      | Список лейблов для присвоения        |

Example Playbook
----------------
```yaml
- hosts: k8s
  gather_facts: true
  become: true
  vars:
    node_labels: 
      node-role.kubernetes.io/infra: ""
      node-role.kubernetes.io/ingress: ""
      node-role.kubernetes.io/monitoring: ""
  roles:
    - k8s/node_labels
  tags:
    - node_labels
```
