# Kubelet

Role install kubelet package and run with default config

## Requirements

Role require configured kubernetes apt repository

## Usage

Overwrite `kubelet_version` and role install this version

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `kubelet_version` | string | `1.20.4-00*` | Version of kubelet debian package |
| `kubelet_force_restart` | bool | false | Flag to force run handler |
