# Set_packages

Install some packages and reboot host if required

## Usage

To reboot and autoremove set `set_packages` to `true`

To install additional packages to some host define `set_packages_addition_packages` and correcpond list of package names

```yaml
set_packages: true
set_packages_addition_packages:
  - "linux-image-5.4.0-94-generic"
```

## Variables

| Name                                | type    | default | description                             |
| ----------------------------------- | ------- | ------- | --------------------------------------- |
| `set_packages`                      | boolean | false   | Run apt with autoremove and reboot host |
| `set_packages_addition_packages`    | list    | []      | list of packages to install on host     |
| `set_packages_hold`                 | boolean | true    | Hold all addition packages              |
| `set_packages_unnecessary_packages` | list    | []      | list of unnecessary packages to remove  |
