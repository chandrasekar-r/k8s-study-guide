# Basic kubectl Commands

kubectl is the command-line tool for interacting with Kubernetes clusters. Here are the essential commands you need to know.

## Cluster Information

```bash
# Get cluster info
kubectl cluster-info

# Get nodes
kubectl get nodes

# Get node details
kubectl describe node <node-name>
```

## Pod Operations

```bash
# Get all pods
kubectl get pods

# Get pods with more details
kubectl get pods -o wide

# Get pod logs
kubectl logs <pod-name>

# Get real-time pod logs
kubectl logs -f <pod-name>

# Describe pod
kubectl describe pod <pod-name>
```

## Deployment Operations

```bash
# Apply a configuration
kubectl apply -f <filename.yaml>

# Delete a configuration
kubectl delete -f <filename.yaml>
```

## Common Options

- `-n, --namespace`: Specify namespace
- `-o wide`: Output in plain-text format with additional information
- `-o yaml`: Output in YAML format
- `-o json`: Output in JSON format
- `--all-namespaces`: List resources across all namespaces

## Output Formatting

```bash
# Get pods with custom columns
kubectl get pods -o custom-columns=NAME:.metadata.name,STATUS:.status.phase

# Get pods in JSON format
kubectl get pods -o json
```