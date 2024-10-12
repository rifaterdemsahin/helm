@rifaterdemsahin ➜ /workspaces/helm (main) $ helm install elasticsearch elastic/elasticsearch -f values-elasticsearch.yaml
coalesce.go:237: warning: skipped value for elasticsearch.roles: Not a table.
Error: INSTALLATION FAILED: template: elasticsearch/templates/statefulset.yaml:313:17: executing "elasticsearch/templates/statefulset.yaml" at <has "master" .Values.roles>: error calling has: Cannot find has on type map

## Solution

This error typically occurs when the `roles` value in your `values.yaml` file is not defined as a map. To resolve this issue, ensure that `roles` is defined correctly. Here is an example of how you might define it:

```yaml
roles:
    master: true
    data: true
    ingest: true
```

Make sure to update your `values.yaml` file accordingly and try reinstalling the Helm chart.

## Example values-elasticsearch.yaml

```yaml
clusterName: "elasticsearch"
nodeGroup: "master"

roles:
    master: true
    ingest: true
    data: true

replicas: 1

esJavaOpts: "-Xmx1g -Xms1g"

resources:
    requests:
        cpu: "100m"
        memory: "1Gi"
    limits:
        cpu: "1000m"
        memory: "1Gi"

volumeClaimTemplate:
    accessModes: [ "ReadWriteOnce" ]
    resources:
        requests:
            storage: 5Gi
```

## Reinstall Helm Chart

```bash
helm uninstall elasticsearch
helm install elasticsearch elastic/elasticsearch -f values-elasticsearch.yaml
```

@rifaterdemsahin ➜ /workspaces/helm/Code (main) $ ^C
@rifaterdemsahin ➜ /workspaces/helm/Code (main) $ helm uninstall elasticsearch
Error: uninstall: Release not loaded: elasticsearch: release: not found
@rifaterdemsahin ➜ /workspaces/helm/Code (main) $ ^C
@rifaterdemsahin ➜ /workspaces/helm/Code (main) $ 