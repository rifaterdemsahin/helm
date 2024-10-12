# Add a Helm repository
🚀 **Add a Helm repository**
```sh
helm repo add <repo-name> <repo-url>
```

🔄 **Update your Helm repositories**
```sh
helm repo update
```

🔍 **Search for a chart in the Helm repositories**
```sh
helm search repo <chart-name>
```

📦 **Install a Helm chart**
```sh
helm install <release-name> <chart-name> --namespace <namespace>
```

⬆️ **Upgrade a Helm release**
```sh
helm upgrade <release-name> <chart-name> --namespace <namespace>
```

📋 **List all Helm releases**
```sh
helm list --namespace <namespace>
```

❌ **Uninstall a Helm release**
```sh
helm uninstall <release-name> --namespace <namespace>
```

📊 **Get the status of a Helm release**
```sh
helm status <release-name> --namespace <namespace>
```

🔄 **Rollback a Helm release to a previous revision**
```sh
helm rollback <release-name> <revision-number> --namespace <namespace>
```

🧪 **Test a Helm release**
```sh
helm test <release-name> --namespace <namespace>
```
