# Helm repo

Role to configure helm repositories

## Requirements

Role require helm binary

## Usage

Overwrite `helm_repo_list` and `helm_repo_username`, `helm_repo_password`

```yaml
- hosts: k8s
  gather_facts: true
  become: true
  vars:
    helm_repo_username: example_user
    helm_repo_password: example_password
    helm_repo_list:
      - name: example_repo1
        url: https://example.repo1.url
      - name: example_repo2
        url: https://example.repo2.url
        username: example_user2
        password: example_password2
  roles:
    - k8s/helm_repo
  tags:
    - helm
    - helm_repo
```

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `helm_repo_list` | list | [] | List of repository |
| `helm_repo_username` | string | "admin" | Username, that used for connect to all helm repo in `helm_repo_list`, if in List not defined `username` |
| `helm_repo_password` | string | "qwerty123" | Password, that used for connect to all helm repo in `helm_repo_list`, if in List not defined `password` |
| `helm_repo_no_log` | string | true | Flag to `no_log` option |
