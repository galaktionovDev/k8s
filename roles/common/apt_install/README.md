# APT install

Role for same dependency installetion deb packages.

If used through `dependencies` in `meta\main.yml`, `apt-install` will be run before main role.

## Requirements

Role require configured apt repository

## Usage

Overwrite:

* `apt_install` - list of pachage_name=package_version

* `apt_install_cache_valid_time` - apt cache valid time

```yaml
dependencies:
  - role: common/apt-install
    apt_install:
      - "kubeadm={{ kubeadm_version }}"
```

You can purge\reinstall packages

```yaml
dependencies:
  - role: common/apt-install
    apt_install_state: absent
    apt_install_purge: true
    apt_install:
      - "kubeadm={{ kubeadm_version }}"
  - role: common/apt-install
    apt_install:
      - "kubeadm={{ kubeadm_version }}"
```

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `apt_install` | list | empty | list of packages with format `package_name[=package_version]` |
| `apt_install_cache_valid_time` | int | `600`| Time to invalidate apt cache |
| `apt_install_force` | bool | `false`| Flag to use force |
| `apt_install_update_cache_retries` | int | `5` | Count of retries to update apt cache |
| `apt_install_state` | string | `present` | state of packages in `apt_install` |
| `apt_install_purge` | bool | `false` | Flag to purge apt packages in `apt_install` |
