Now, let's test your understanding with a quiz! Please answer these questions:

What are the main components of the Kubernetes Control Plane?
Name three key differences between Docker and Kubernetes.
What is the role of kubelet in a worker node?
Why does Kubernetes need etcd, and what does it store?
In terms of high availability, how does Kubernetes differ from basic Docker?

Take your time to answer these questions. Feel free to refer back to the notes, but try to answer from memory first. I'll provide feedback on your answers and clarify any points that need more explanation. CopyRetryRAPI server, etcd, scheduler and control manager.docker runs on single host where are k8s can be installed on mutliple master and worker node. Docker can't be scaled horizonatally where as k8s can be. docker doesn't support autoscaling/auto healing where as k8s does.Kubelte is repsonible for maintainign the pod state. Basically it manages teh podetcd is a key/value store that is used to remember the state of k8s. used for restoreDOcker doens't support HA where as k8s does with load balancing and autoscalingEditGreat answers! Let me provide feedback for each:

✅ Perfect! You correctly identified all four main components of the Control Plane:

API server
etcd
Scheduler
Controller Manager


✅ Excellent! Your understanding of Docker vs Kubernetes differences is solid. You highlighted:

Single host vs multi-node architecture
Scaling capabilities
Auto-healing/auto-scaling features


✋ Partially correct. While you're right that kubelet manages pods, let's expand on its responsibilities:

Ensures containers are running in a pod
Reports node and pod status to the master
Handles container operations (start, stop, restart)
Executes health checks


✋ Partially correct. While you understand that etcd is for state storage, let's clarify:

It's not just for restore purposes
It stores ALL cluster data, including:

Node information
Pod states
ConfigMaps
Secrets
All cluster configuration


It's the "source of truth" for the entire cluster


✅ Correct! Good understanding of HA differences. Kubernetes provides:

Load balancing
Auto-scaling
Multi-node redundancy
Self-healing capabilities



Overall Score: 4/5 - Very good understanding!
Would you like to explore any of these concepts in more depth? I can provide more detailed information about any area you'd like to understand better, particularly about kubelet's full role or etcd's comprehensive functionality.