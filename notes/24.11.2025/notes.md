# Introduction to Kubernetes

## What is Kubernetes?
- Container orchestration platform
- Manages deployment, scaling and operations of containers
- Originally developed by Google, now maintained by CNCF

## Why do we need orchestration?
- Manual container management doesn't scale
- Need automatic scaling, healing and load balancing
- Managing hundreds of containers manually is impossible

## Key Components
- **Cluster** - Set of nodes running containerized apps
- **Node** - A machine in the cluster (Master or Worker)
- **Pod** - Smallest deployable unit, contains containers
- **Deployment** - Manages pod replicas
- **Service** - Exposes pods to network

## Architecture
- Master Node: API Server, Scheduler, Controller Manager, etcd
- Worker Node: Kubelet, Container Runtime, Kube Proxy

## Basic Commands
```bash
# Check cluster info
kubectl cluster-info

# Get nodes
kubectl get nodes

# Get pods
kubectl get pods
```
