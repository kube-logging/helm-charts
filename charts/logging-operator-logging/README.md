# logging-operator-logging
The chart has been merged into logging-operator and relocated [here](https://github.com/kube-logging/logging-operator/tree/master/charts/logging-operator).

Most of the existing chart values and functionalities are available in the new `logging-operator` under the `logging` field
but an extra `enabled` flag is required to activate it:
```
logging:
  enabled: true
```

For an example on how to configure a logging resource in the new chart see [the logging operator e2e test values file](https://github.com/kube-logging/logging-operator/blob/master/hack/values.yaml#L10)

Changes after the migration:
- Name of the logging resource now comes from the _release name_ or from the `nameOverride` field if it is set.
  ```
  -  name: {{ include "logging-operator-logging.name" . }}
  +  name: {{ include "logging-operator.releasename" . }}
  ```
- Names of other resources are now aligned with the new chart. This means they will use the new chart's name or the `nameOverride` field in the new chart if set.
  ```
  -  name: {{ include "logging-operator-logging.name" . }}
  +  name: {{ include "logging-operator.name" . }}q
  ```
- same thing applies to labels
  ```
  labels:
  -{{ include "logging-operator-logging.labels" $ | indent 4 }}
  +{{ include "logging-operator.labels" $ | indent 4 }}
  ```
- Oracle SCC and automatic TLS setup between fluentbit and fluentd has been removed
- the new `FluentbitAgent` resource is used instead of the embedded legacy version see: [Migrating from spec.fluentbit to FluentbitAgent](https://kube-logging.dev/docs/logging-infrastructure/fluentbit/#migrating)
