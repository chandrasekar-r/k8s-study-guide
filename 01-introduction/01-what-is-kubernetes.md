# What is Kubernetes (K8s)?

Kubernetes is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications. Originally developed by Google, it is now maintained by the Cloud Native Computing Foundation (CNCF).

## Key Features

1. **Container Orchestration**
   - Automates the deployment and scaling of containerized applications
   - Manages containerized applications across multiple hosts
   - Provides a framework to run distributed systems resiliently

2. **Self-healing**
   - Automatically restarts failed containers
   - Replaces and reschedules containers when nodes die
   - Kills containers that don't respond to health checks
   
3. **Horizontal Scaling**
   - Can scale applications up or down based on demand
   - Manual or automatic scaling options
   - Resource-aware scheduling

4. **Load Balancing**
   - Distributes network traffic to ensure stable deployment
   - Internal load balancing for service discovery
   - External load balancing for public services

5. **Automated Rollouts/Rollbacks**
   - Changes to application or config can be rolled out gradually
   - Monitors application health during rollout
   - Automatic rollback in case of deployment issues

6. **Secret Management**
   - Manages sensitive information like passwords
   - Handles SSH keys and tokens
   - Deploys and updates secrets without rebuilding containers

7. **Storage Orchestration**
   - Automatically mounts storage systems
   - Local or cloud storage options
   - Persistent volume management