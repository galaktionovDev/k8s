# Feature resources

Role announce and calculate resources

## Requirements

Role required define variable `feature_resources`

## Usage

Include role and define in vars `feature_resources` with list

```yaml
- name: announce  feature resources
  ansible.builtin.import_role:
    name: common/feature_resources
  vars:
    feature_resources:
      - type: infra
        cpu: "{{ oidc_auth_dex_requests_cpu }}"
        memory: "{{ oidc_auth_dex_requests_memory }}"
      - type: infra
        cpu: "{{ oidc_auth_gangway_requests_cpu }}"
        memory: "{{ oidc_auth_gangway_requests_memory }}"
```

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `feature_allocated` | dict of dicts | `{}`| Calculated |
| `feature_resources` | list | empty | list of packages with format `package_name[=package_version]` |
| `feature_resources.*.type` | bool | `false`| Flag to use force |
| `feature_resources.*.cpu` | bool | `false`| Flag to use force |
| `feature_resources.*.memory` | bool | `false`| Flag to use force |
