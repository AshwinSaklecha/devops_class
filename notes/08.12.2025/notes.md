# Understanding Kubernetes Services

## What are Services?
- Services expose pods to network traffic
- Pods are ephemeral - IPs change when recreated
- Services provide stable endpoint to access pods

## Why Services?
- Pod IPs are not reliable
- Need stable way to access application
- Load balancing across pod replicas

## Types of Services

### 1. ClusterIP (default)
- Internal access only
- Exposes on cluster-internal IP

### 2. NodePort
- Exposes on each node's IP at static port
- Accessible from outside cluster

### 3. LoadBalancer
- Exposes externally using cloud load balancer
- Works with cloud providers (AWS, GCP, Azure)

## Service YAML
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
  - port: 80
    targetPort: 80
  type: ClusterIP
```

## Commands
```bash
# Create service
kubectl apply -f service.yaml

# Get services
kubectl get svc

# Describe service
kubectl describe svc nginx-service

# Expose deployment as service
kubectl expose deployment nginx --port=80 --type=NodePort
```
