# Setting Up Minikube

Minikube is a tool that runs a single-node Kubernetes cluster locally on your machine. It's perfect for learning Kubernetes and developing applications locally.

## Prerequisites

- Docker Desktop (or VirtualBox)
- kubectl command-line tool
- At least 2 CPUs and 2GB of free memory

## Installation Steps

### macOS
```bash
# Using Homebrew
brew install minikube

# Start Minikube
minikube start
```

### Verify Installation
```bash
# Check status
minikube status

# Check version
minikube version
```

## Basic Minikube Commands

```bash
# Start cluster
minikube start

# Stop cluster
minikube stop

# Delete cluster
minikube delete

# Access dashboard
minikube dashboard

# Get cluster IP
minikube ip
```

## Troubleshooting

1. If minikube fails to start:
   ```bash
   minikube delete
   minikube start --driver=docker
   ```

2. Check available drivers:
   ```bash
   minikube config get driver
   ```

3. View logs:
   ```bash
   minikube logs
   ```