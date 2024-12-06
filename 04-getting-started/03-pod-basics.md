# Understanding Pods in Kubernetes

A Pod is the smallest deployable unit in Kubernetes. It represents a single instance of a running process in your cluster.

## Basic Pod YAML Structure

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod-name
  labels:
    app: my-app
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

## Key Components of Pod YAML

1. **apiVersion**: Specifies the Kubernetes API version
2. **kind**: Defines the type of resource (Pod)
3. **metadata**: Contains pod information like name and labels
4. **spec**: Defines the desired state of the pod

## Example: Deploying Nginx Pod

1. Create a file named `nginx-pod.yaml`:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

2. Deploy the pod:
```bash
kubectl apply -f nginx-pod.yaml
```

3. Verify deployment:
```bash
kubectl get pods
kubectl describe pod nginx-pod
```

4. Access the pod:
```bash
# Port forward to access nginx
kubectl port-forward nginx-pod 8080:80
```

## Pod Lifecycle

1. **Pending**: Pod accepted but containers not running
2. **Running**: Pod bound to node, all containers created
3. **Succeeded**: All containers terminated successfully
4. **Failed**: All containers terminated, at least one failed
5. **Unknown**: Pod state cannot be determined

## Best Practices

1. Use descriptive pod names
2. Always specify resource limits
3. Use labels for organization
4. Keep pods stateless when possible
5. Use health checks