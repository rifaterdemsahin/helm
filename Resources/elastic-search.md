# Helm Charts for Elasticsearch and Grafana

## Elasticsearch

### Chart Repository
Add the official Elasticsearch Helm chart repository:
```sh
helm repo add elastic https://helm.elastic.co
helm repo update
```

### Install Elasticsearch
Create a `values-elasticsearch.yaml` file with the following content:
```yaml
clusterName: "elasticsearch"
nodeGroup: "master"

roles:
    master: "true"
    ingest: "true"
    data: "true"

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

Install Elasticsearch using the Helm chart:
```sh
helm install elasticsearch elastic/elasticsearch -f values-elasticsearch.yaml
```

## Grafana

### Chart Repository
Add the official Grafana Helm chart repository:
```sh
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
```

### Install Grafana
Create a `values-grafana.yaml` file with the following content:
```yaml
adminUser: admin
adminPassword: admin

service:
    type: NodePort
    port: 80
    nodePort: 30000

resources:
    requests:
        cpu: "100m"
        memory: "256Mi"
    limits:
        cpu: "500m"
        memory: "512Mi"
```

Install Grafana using the Helm chart:
```sh
helm install grafana grafana/grafana -f values-grafana.yaml
```

## Accessing Grafana
To access Grafana, use the following command to get the Minikube IP:
```sh
minikube ip
```
Then, open your browser and navigate to `http://<minikube-ip>:30000`.
