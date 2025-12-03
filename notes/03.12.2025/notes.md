# Kubernetes ReplicaSets

## What is a ReplicaSet?
- Ensures specified number of pod replicas are running
- Provides self-healing - restarts failed pods
- Maintains stable set of replica pods

## ReplicaSet vs Pod
- Pod alone has no auto-recovery
- ReplicaSet monitors and maintains desired count
- If pod dies, ReplicaSet creates new one

## YAML Definition
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-rs
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
```

## Commands
```bash
# Create replicaset
kubectl apply -f replicaset.yaml

# Get replicasets
kubectl get rs

# Scale replicaset
kubectl scale rs nginx-rs --replicas=5

# Delete replicaset
kubectl delete rs nginx-rs
```

## Key Points
- Selector must match template labels
- Direct ReplicaSet usage is rare, use Deployments instead
- Deployments manage ReplicaSets internally
