# Working with Deployment YAML

## Basic Deployment Structure

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

## Key Components Explained

1. **metadata**
   - name: Identifies the deployment
   - labels: Key-value pairs for organizing resources

2. **spec**
   - replicas: Number of desired identical pods
   - selector: Defines how deployment finds pods to manage

3. **template**
   - Pod template specification
   - Defines container configuration

## Common Operations

### Creating Deployment
```bash
kubectl apply -f deployment.yaml
```

### Checking Status
```bash
# Get deployments
kubectl get deployments

# Watch deployment progress
kubectl get deployments -w

# Get deployment details
kubectl describe deployment nginx-deployment
```

### Scaling
```bash
# Scale using command
kubectl scale deployment nginx-deployment --replicas=5

# Scale by editing YAML
# Change replicas: 3 to desired number
```