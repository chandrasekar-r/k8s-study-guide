# Understanding Kubernetes Deployments

## Container vs Pod vs Deployment

### Container
- Smallest unit that packages your application code and its dependencies
- Isolated environment for running an application
- Example: Docker container running nginx

### Pod
- Smallest deployable unit in Kubernetes
- Can contain one or more containers
- Shares network namespace and storage
- Temporary in nature - can die and won't be recreated

### Deployment
- Higher-level abstraction that manages Pods
- Provides declarative updates for Pods
- Ensures desired number of Pods are running
- Handles rolling updates and rollbacks
- Creates and manages ReplicaSets

## Why Use Deployments?

1. **Self-healing**
   - If a Pod crashes, Deployment automatically creates a new one
   - Maintains desired number of replicas

2. **Scalability**
   - Easy to scale up or down by changing replica count
   - Handles distribution of Pods across nodes

3. **Rolling Updates**
   - Update application version without downtime
   - Automatic rollback if issues occur

4. **Version Control**
   - Track and control changes to Pod configurations
   - Roll back to previous versions if needed

## Understanding ReplicaSets

ReplicaSet is the engine behind Deployment that ensures:
- Desired number of Pods are running
- Pods are identical (based on template)
- Automatic replacement of failed Pods

Deployment → ReplicaSet → Pods