To install **NGINX** using **Helm**, you need to follow these steps. Assuming you have Helm and Kubernetes set up on your system, here's how to install NGINX:

1. **Add the NGINX Helm repository:**

   ```bash


   helm repo add nginx-stable https://helm.nginx.com/stable
   ```

2. **Update your Helm repositories to ensure you have the latest version of the chart:**

   ```bash
   helm repo update
   ```

3. **Install the NGINX Helm chart:**

   To install the NGINX Ingress Controller, run the following command:

   ```bash
   helm install my-nginx nginx-stable/nginx-ingress
   ```

   In this command:
   - `my-nginx` is the release name you can choose, and
   - `nginx-stable/nginx-ingress` is the chart name from the `nginx-stable` repository.

4. **Check the installation:**

   After installation, you can check the status of the NGINX deployment with:

   ```bash
   helm ls
   ```

5. **Verify the NGINX ingress controller pods are running:**

   ```bash
   kubectl get pods -l app.kubernetes.io/name=nginx-ingress
   ```

This will install the NGINX Ingress controller on your Kubernetes cluster, allowing you to manage ingress traffic into your applications. Let me know if you'd like more customization or need help with specific configuration settings.


To create a Helm `values.yaml` file and perform an upgrade, I'll guide you through the steps and provide a sample `values.yaml` file for an NGINX installation. I'll also give you a basic Markdown (MD) file to document the process.

### 1. **Create the `values.yaml` File**

Here's a sample `values.yaml` file for NGINX:

```yaml
# values.yaml
controller:
  replicaCount: 2
  service:
    type: LoadBalancer
    externalTrafficPolicy: Local
  metrics:
    enabled: true
    serviceMonitor:
      enabled: true

defaultBackend:
  enabled: true
  replicaCount: 1

# Additional configuration for customization can be added below.
```

In this file:
- The `controller.replicaCount` is set to `2`, meaning NGINX Ingress will run two replicas.
- `service.type` is set to `LoadBalancer` to expose the service externally.
- `metrics.enabled` and `serviceMonitor.enabled` are set to `true` to enable monitoring.

### 2. **Helm Upgrade Command**

To upgrade the existing Helm release using the new `values.yaml` file, use the following command:

```bash
helm upgrade my-nginx nginx-stable/nginx-ingress -f values.yaml
```

Here:
- `my-nginx` is the release name of your Helm deployment.
- `nginx-stable/nginx-ingress` is the chart you're using.
- `-f values.yaml` specifies the values file you want to use for this upgrade.

### 3. **Markdown Documentation**

Here’s a simple Markdown file to document the steps.

```markdown
# NGINX Ingress Controller - Helm Installation and Upgrade

## Overview
This guide covers how to install and upgrade the NGINX Ingress Controller using Helm with custom values.

## Prerequisites
- Kubernetes cluster
- Helm installed and configured
- NGINX Helm repository added

## Installation Steps

1. **Add the NGINX Helm repository:**

   ```bash
   helm repo add nginx-stable https://helm.nginx.com/stable
   ```

2. **Update the Helm repositories:**

   ```bash
   helm repo update
   ```

3. **Install NGINX Ingress Controller:**

   ```bash
   helm install my-nginx nginx-stable/nginx-ingress
   ```

## Upgrade Process

1. **Create or modify the `values.yaml` file:**

   ```yaml
   controller:
     replicaCount: 2
     service:
       type: LoadBalancer
       externalTrafficPolicy: Local
     metrics:
       enabled: true
       serviceMonitor:
         enabled: true

   defaultBackend:
     enabled: true
     replicaCount: 1
   ```

2. **Upgrade the existing Helm release with the `values.yaml` file:**

   ```bash
   helm upgrade my-nginx nginx-stable/nginx-ingress -f values.yaml
   ```

3. **Verify the upgrade:**

   After running the upgrade, check the status of your pods:

   ```bash
   kubectl get pods -n <namespace>
   ```

## Additional Notes

- You can further customize the `values.yaml` file as per your needs.
- Monitor the deployment and service using the enabled metrics.
```

### Next Steps
- Use the provided `values.yaml` to customize your Helm deployment.
- Run the `helm upgrade` command to apply the changes.
- Update the Markdown file with any specific details related to your environment.

Let me know if you'd like more customization!