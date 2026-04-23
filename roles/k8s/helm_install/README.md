# Helm install

Download, extract and link helm binary

## Requirements

## Usage

Overwrite:

* `helm_version` - helm version of binary

* `helm_url` - URL for helm tag.gz

## Variables

| Name | type | default | description |
|------|------|---------|-------------|
| `helm_path` | string | /app/helm | Directory for store helm tar.gz and binary |
| `helm_version` | string | v3.5.4 | Version of Helm |
| `helm_url` | string | "https://get.helm.sh/" | URL for helm tag.gz |
| `helm_diff_url` | string | https://github.com/databus23/helm-diff/releases/download/v3.4.2 | url for download helm diff archive |
| `helm_diff_filename` | string | helm-diff-linux-amd64.tgz | filename on `helm_diff_url` with helm diff archive  |
| `helm_install_diff` | string | true | Flag to install helm diff plugin |
| `helm_completion` | string |  true | Flag to install bash auto completion |
| `helm_url_headers` | dict |  {} | Headers for `helm_url` |
| `helm_diff_url_headers` | dict |  {} | Headers for `helm_diff_url` |
| `helm_install_proxy` | string | "" | Http(s) proxy for `get_url` |
