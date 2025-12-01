# Kubernetes Pods - Deep Dive

## What is a Pod?
- Smallest deployable unit in K8s
- Contains one or more containers
- Containers in pod share network and storage

## Pod Lifecycle
1. Pending - Pod accepted but not running
2. Running - At least one container running
3. Succeeded - All containers completed successfully
4. Failed - At least one container failed
5. Unknown - State cannot be determined

## Creating Pods
```yaml
# pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

## Commands
```bash
# Create pod from yaml
kubectl apply -f pod.yaml

# Get pods
kubectl get pods

# Describe pod
kubectl describe pod nginx-pod

# Get pod logs
kubectl logs nginx-pod

# Delete pod
kubectl delete pod nginx-pod

# Exec into pod
kubectl exec -it nginx-pod -- bash
```

## Multi-container Pods
- Sidecar pattern - helper container
- Ambassador pattern - proxy container
- Adapter pattern - standardize output
