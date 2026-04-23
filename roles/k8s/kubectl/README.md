# kubectl

Role install kubectl package

## Requirements

Role require configured kubernetes apt repository

## Usage

Overwrite `kubectl_version` and role install this version

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `kubectl_version` | string | `1.20.4*` | Version of kubectl debian package |
| `kubectl_auto_completion` | bool | `true`| Flag to install kubectl auto-completion |
| `kubectl_auto_completion_addition_packages` | list | `[ bash-completion ]`| List of packages that reqired to configure kubectl auto-completion |
| `kubectl_auto_completion_path` | string | `/etc/bash_completion.d/kubectl`| Path of kubectl auto-completion source file |
| `kubectl_auto_completion_force` | bool | `true` | Flag to force overwrite auto-completion source file |
