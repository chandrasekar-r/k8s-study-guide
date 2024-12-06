# Pod Lifecycle and Self-healing

## Pod Deletion Experiment

When you delete a Pod managed by a Deployment:

1. **Initial State**
   - Deployment maintains desired number of replicas
   - Each Pod has unique name and ID

2. **Pod Deletion**
   ```bash
   kubectl delete pod <pod-name>
   ```

3. **Automatic Recovery**
   - Deployment notices Pod count < desired
   - ReplicaSet creates new Pod automatically
   - New Pod gets new name and ID

## Observing Changes

```bash
# Watch Pods in real-time
kubectl get pods -w

# See events
kubectl describe deployment nginx-deployment
```

## What Happens Behind the Scenes

1. **Pod Deletion**
   - Pod enters Terminating state
   - Containers stop gracefully
   - Pod resources cleaned up

2. **ReplicaSet Action**
   - Detects Pod count discrepancy
   - Triggers creation of new Pod
   - Ensures desired state maintained

3. **New Pod Creation**
   - Pod scheduled on available node
   - Containers started
   - Application becomes available

## Common Scenarios

1. **Single Pod Deletion**
   - Immediate replacement
   - Minimal disruption

2. **Multiple Pod Deletions**
   - Parallel replacement
   - Load distribution maintained

3. **Node Failure**
   - All Pods on node replaced
   - Distributed across healthy nodes