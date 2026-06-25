# dnf install

Role for same dependency installetion deb packages.

If used through `dependencies` in `meta\main.yml`, `dnf-install` will be run before main role.

## Requirements

Role require configured dnf repository

## Usage

Overwrite:

* `dnf_install` - list of pachage_name=package_version


```yaml
dependencies:
  - role: common/dnf-install
    dnf_install:
      - "kubeadm={{ kubeadm_version }}"
```

You can purge\reinstall packages

```yaml
dependencies:
  - role: common/dnf-install
    dnf_install_state: absent
    dnf_install:
      - "kubeadm={{ kubeadm_version }}"
  - role: common/dnf-install
    dnf_install:
      - "kubeadm={{ kubeadm_version }}"
```

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `dnf_install` | list | empty | list of packages with format `package_name[=package_version]` |
| `dnf_install_update_cache_retries` | int | `5` | Count of retries to update dnf cache |
| `dnf_install_state` | string | `present` | state of packages in `dnf_install` |
