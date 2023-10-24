## Welcome to the UDS Capability Template!

1. Update [CHANGELOG.md](CHANGELOG.md), [CONTRIBUTING.md](CONTRIBUTING.md), [DEVELOPMENT_MAINTENANCE.md](docs/DEVELOPMENT_MAINTENANCE.md)
1. Populate [CODEOWNERS](CODEOWNERS), [README.md](README.md)
1. Verify [LICENSE](LICENSE)
1. Add [manifests](manifests/), [values](values/), and [docs](docs/)
1. Complete [zarf.yaml](zarf.yaml)
1. Flesh out the [pipeline](.github/)
1. Delete this section

***

# UDS Capability Postgres Operator

This UDS Capability repository contains a deployment of [Zalando Postgres Operator](https://github.com/zalando/postgres-operator) for running production ready postgres instances in a kubernetes cluster.

## Prerequisites

- Zarf is installed locally with a minimum version of v0.30.1
- Working kube context (kubectl get nodes <-- this command works)
- Kubernetes cluster has been zarf init-ed

## Create

```console
zarf package create --confirm
```

## Deploy

```console
# Modify zarf-config.yaml as needed

# Deploy the zarf package, EITHER the..
#  locally-created package .zst file
zarf package deploy --confirm zarf-package-postgres-operator-*.tar.zst
#  OR a published OCI package (browse release at
#    https://github.com/defenseunicorns/uds-package-dubbd/pkgs/container/packages%2Fpostgres-operator)
zarf package deploy oci://ghcr.io/defenseunicorns/packages/postgres-operator:0.0.1-amd64 --oci-concurrency=15
```

## Remove

```console
zarf package remove postgres-operator --confirm
```
