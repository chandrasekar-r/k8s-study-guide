# Kubernetes Worker Node Components

Worker nodes are the machines that run your applications and cloud workloads.

## Components Overview

### 1. kubelet

The primary node agent that runs on each node. It ensures containers are running in a Pod.

**Responsibilities:**
- Pod management
- Container health checks
- Resource reporting
- Node status updates

### 2. kube-proxy

Network proxy that runs on each node, implementing part of the Kubernetes Service concept.

**Responsibilities:**
- Network rules maintenance
- Connection forwarding
- Load balancing
- Service abstraction