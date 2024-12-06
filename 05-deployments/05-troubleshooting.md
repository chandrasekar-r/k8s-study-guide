# Deployment Troubleshooting Guide

## Common Issues and Solutions

### 1. Pods Stuck in Pending State

#### Symptoms
```bash
$ kubectl get pods
NAME                        READY   STATUS    RESTARTS   AGE
my-app-7b6f8d4589-x2jd9    0/1     Pending   0          5m
```

#### Diagnosis Steps
```bash
# Check pod details
kubectl describe pod my-app-7b6f8d4589-x2jd9

# Check node resources
kubectl describe nodes
```

#### Common Causes and Solutions
1. **Insufficient Resources**
   - Symptom: `Insufficient cpu`, `Insufficient memory`
   - Solution: Adjust resource requests/limits or add nodes
   ```yaml
   resources:
     requests:
       memory: "64Mi"
       cpu: "250m"
     limits:
       memory: "128Mi"
       cpu: "500m"
   ```

2. **Node Selector Issues**
   - Symptom: `0/3 nodes are available: 3 node(s) didn't match node selector`
   - Solution: Check node labels or update selector
   ```bash
   kubectl label nodes <node-name> environment=prod
   ```

### 2. Pods Crashing or Restarting

#### Symptoms
```bash
$ kubectl get pods
NAME                        READY   STATUS    RESTARTS   AGE
my-app-7b6f8d4589-x2jd9    0/1     CrashLoopBackOff   3          5m
```

#### Diagnosis Steps
```bash
# Check pod logs
kubectl logs my-app-7b6f8d4589-x2jd9

# Check previous container logs if present
kubectl logs my-app-7b6f8d4589-x2jd9 --previous

# Get detailed pod information
kubectl describe pod my-app-7b6f8d4589-x2jd9
```

#### Common Causes and Solutions
1. **Application Errors**
   - Check application logs for runtime errors
   - Verify environment variables and configurations
   ```bash
   kubectl exec -it my-app-7b6f8d4589-x2jd9 -- env
   ```

2. **Resource Constraints**
   - Check if container is being OOM killed
   - Adjust memory limits in deployment

### 3. Rolling Update Issues

#### Symptoms
```bash
$ kubectl rollout status deployment/my-app
Waiting for deployment "my-app" rollout to finish: 1 old replicas are pending termination...
```

#### Diagnosis Steps
```bash
# Check rollout history
kubectl rollout history deployment/my-app

# Check rollout status
kubectl rollout status deployment/my-app

# Get deployment events
kubectl describe deployment my-app
```

#### Common Solutions
1. **Rollback to Previous Version**
   ```bash
   kubectl rollout undo deployment/my-app
   ```

2. **Adjust Rolling Update Strategy**
   ```yaml
   spec:
     strategy:
       type: RollingUpdate
       rollingUpdate:
         maxSurge: 1
         maxUnavailable: 0
   ```

### 4. Image Pull Issues

#### Symptoms
```bash
$ kubectl get pods
NAME                        READY   STATUS         RESTARTS   AGE
my-app-7b6f8d4589-x2jd9    0/1     ImagePullBackOff   0          5m
```

#### Diagnosis and Solutions
1. **Check Image Name and Tag**
   ```bash
   kubectl describe pod my-app-7b6f8d4589-x2jd9
   ```
   - Verify image name and tag are correct
   - Check if image exists in registry

2. **Private Registry Authentication**
   ```bash
   kubectl create secret docker-registry regcred \
     --docker-server=<registry-server> \
     --docker-username=<username> \
     --docker-password=<password>
   ```
   Then add to deployment:
   ```yaml
   spec:
     imagePullSecrets:
     - name: regcred
   ```

## Quick Troubleshooting Commands

```bash
# Get pod status
kubectl get pods

# Get detailed pod info
kubectl describe pod <pod-name>

# Get pod logs
kubectl logs <pod-name>

# Check events
kubectl get events --sort-by=.metadata.creationTimestamp

# Check deployment status
kubectl rollout status deployment/<deployment-name>

# Debug with temporary pod
kubectl run tmp-debug --rm -i --tty --image=busybox -- /bin/sh
```

## Best Practices for Prevention

1. **Always use Resource Limits**
   ```yaml
   resources:
     requests:
       memory: "64Mi"
       cpu: "250m"
     limits:
       memory: "128Mi"
       cpu: "500m"
   ```

2. **Implement Health Checks**
   ```yaml
   livenessProbe:
     httpGet:
       path: /healthz
       port: 8080
     initialDelaySeconds: 3
     periodSeconds: 3
   ```

3. **Use Proper Labels and Selectors**
   ```yaml
   labels:
     app: my-app
     environment: prod
     version: v1.0.0
   ```

4. **Version Control Your Deployments**
   - Use semantic versioning for images
   - Keep deployment YAML in version control
   - Document configuration changes