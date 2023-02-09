# logging-demo

![version: 4.0.0-rc18](https://img.shields.io/badge/version-4.0.0--rc18-informational?style=flat-square) ![type: application](https://img.shields.io/badge/type-application-informational?style=flat-square) ![app version: 4.0.0-rc17](https://img.shields.io/badge/app%20version-4.0.0--rc17-informational?style=flat-square) ![kube version: >=1.16.0-0](https://img.shields.io/badge/kube%20version->=1.16.0--0-informational?style=flat-square) [![artifact hub](https://img.shields.io/badge/artifact%20hub-logging--demo-informational?style=flat-square)](https://artifacthub.io/packages/helm/kube-logging/logging-demo)

Logging operator demo application

**Homepage:** <https://kube-logging.github.io>

## TL;DR;

```bash
helm repo add kube-logging https://kube-logging.github.io/helm-charts
helm install --generate-name --wait kube-logging/logging-demo
```

## Introduction

This chart demonstrates the use of the [Logging Operator](https://github.com/kube-logging/helm-charts/tree/main/charts/logging-operator) with a
[Log-Generator](https://github.com/banzaicloud/log-generator) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- [Logging Operator](https://github.com/kube-logging/logging-operator) available on the cluster.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| nameOverride | string | `""` | A name in place of the chart name for `app:` labels. |
| fullnameOverride | string | `""` | A name to substitute for the full names of resources. |
| loggingOperator.clusterDomain | string | `"cluster.local"` |  |
| loggingOperator.controlNamespace | string | `nil` |  |
| loggingOperator.fluentd | object | `{}` | Fluentd configuration |
| loggingOperator.fluentbit | object | `{}` | Fluentbit configuration |
| loggingOperator.tls.enabled | bool | `true` | Enable secure connection between fluentd and fluent-bit |
| loggingOperator.tls.fluentdSecretName | string | `""` | Specified secret name, which contain tls certs |
| loggingOperator.tls.fluentbitSecretName | string | `""` | Specified secret name, which contain tls certs |
| loggingOperator.tls.sharedKey | string | `""` |  |
| file.enabled | bool | `false` |  |
| minio.enabled | bool | `false` |  |
| minio.existingSecret | string | `"logging-s3"` |  |
| minio.persistence.enabled | bool | `false` |  |
| minio.environment.MINIO_REGION | string | `"test_region"` |  |
| minio.defaultBucket.enabled | bool | `true` |  |
| minio.defaultBucket.name | string | `"demo"` |  |
| minio.resources.requests.memory | string | `"256Mi"` |  |
| elasticsearch.enabled | bool | `false` | Enable ElasticSearch logging output |
| loki.enabled | bool | `false` | Enable Grafana Loki logging output |
| kafka.enabled | bool | `false` | Enable Kafka logging output |
| cloudwatch.enabled | bool | `false` | Enable AWS Cloudwatch logging output |
| cloudwatch.aws.secret_key | string | `""` |  |
| cloudwatch.aws.access_key | string | `""` |  |
| cloudwatch.aws.region | string | `""` |  |
| cloudwatch.aws.log_group_name | string | `""` |  |
| cloudwatch.aws.log_stream_name | string | `""` |  |
| logdna.enabled | bool | `false` | Enable LogDNA logging output |
| logdna.api_key | string | `""` |  |
| logdna.app | string | `""` |  |
| logdna.hostname | string | `""` |  |
| logGenerator.enabled | bool | `true` | Enable Demo Log-Gen application |
