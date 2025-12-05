# Kubernetes Deployments

## What is a Deployment?
- Higher level abstraction over ReplicaSet
- Provides declarative updates for pods
- Supports rolling updates and rollbacks

## Why Deployments?
- ReplicaSets don't handle updates well
- Deployments manage version changes smoothly
- Can rollback to previous versions easily

## Deployment YAML
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
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
        image: nginx:1.19
```

## Commands
```bash
# Create deployment
kubectl apply -f deployment.yaml

# Get deployments
kubectl get deployments

# Update image (rolling update)
kubectl set image deployment/nginx-deployment nginx=nginx:1.20

# Check rollout status
kubectl rollout status deployment/nginx-deployment

# Rollback
kubectl rollout undo deployment/nginx-deployment

# View rollout history
kubectl rollout history deployment/nginx-deployment
```

## Rolling Update Strategy
- New pods created gradually
- Old pods terminated gradually
- Zero downtime during updates
