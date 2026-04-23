# Kubeadm

Role install kubeadm package

## Requirements

Role require configured kubernetes apt repository

## Usage

Overwrite `kubeadm_version` and role install this version

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `kubeadm_version` | string | `1.20.4*` | Version of kubeadm debian package |
| `kubeadm_sysctl_parameters` | list | | List of string in `sysctl -w` format |
