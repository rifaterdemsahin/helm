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