# Add a Helm repository
helm repo add <repo-name> <repo-url>

# Update your Helm repositories
helm repo update

# Search for a chart in the Helm repositories
helm search repo <chart-name>

# Install a Helm chart
helm install <release-name> <chart-name> --namespace <namespace>

# Upgrade a Helm release
helm upgrade <release-name> <chart-name> --namespace <namespace>

# List all Helm releases
helm list --namespace <namespace>

# Uninstall a Helm release
helm uninstall <release-name> --namespace <namespace>

# Get the status of a Helm release
helm status <release-name> --namespace <namespace>

# Rollback a Helm release to a previous revision
helm rollback <release-name> <revision-number> --namespace <namespace>
