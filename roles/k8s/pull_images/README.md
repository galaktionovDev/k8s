# Pull_images

Role pull image via crictl

## Requirements

* installed and configured `crictl`

* installed and configured one of CRI(docker\containerd)

## Usage

Add full path to docker image to `pull_images_list` variable and run role

```yaml
pull_images_list:
  - k8s.gcr.io/coredns:1.7.0
```

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `pull_images_list` | list | empty | List of images |
| `pull_image_registry` | string | '' | String for overwrite registry hostname before pull images |
