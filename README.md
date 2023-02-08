# Helm Charts

![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/kube-logging/helm-charts/release.yaml?branch=master&style=flat-square)
[![Artifact HUB](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/kube-logging)](https://artifacthub.io/packages/search?repo=kube-logging)
![Kubernetes Version](https://img.shields.io/badge/k8s%20version-%3E=1.19-3f68d7.svg?style=flat-square)

Various Helm [charts](https://helm.sh/docs/topics/charts/) for Kube logging.


## Usage

[Helm](https://helm.sh) must be installed to use these charts.
Please refer to the [official documentation](https://helm.sh/docs/intro/install/) to get started.

```bash
helm repo add kube-logging https://kube-logging.github.io/helm-charts
```

You can then see the charts by running:

```bash
helm search repo kube-logging
```

You can install charts using the following command:

```bash
helm install --generate-name kube-logging/CHART
# OR
helm install --name my-release kube-logging/CHART
```

> **Tip**: List all installed releases using `helm list`.

To uninstall a chart release:

```bash
helm delete my-release
```
