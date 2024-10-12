@rifaterdemsahin ➜ /workspaces/helm (main) $ helm install elasticsearch elastic/elasticsearch -f values-elasticsearch.yaml
coalesce.go:237: warning: skipped value for elasticsearch.roles: Not a table.
Error: INSTALLATION FAILED: template: elasticsearch/templates/statefulset.yaml:313:17: executing "elasticsearch/templates/statefulset.yaml" at <has "master" .Values.roles>: error calling has: Cannot find has on type map


