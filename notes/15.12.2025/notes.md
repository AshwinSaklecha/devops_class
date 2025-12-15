# Horizontal Pod Autoscaler (HPA)

## What is HPA?
- Automatically scales pods based on metrics
- Scales deployment/replicaset horizontally
- Adjusts replica count based on CPU/memory usage

## How HPA Works
1. Metrics server collects resource usage
2. HPA controller checks metrics periodically
3. Calculates desired replicas based on target
4. Scales up or down as needed

## Prerequisites
- Metrics server must be installed
- Resource requests must be defined in pods

## HPA YAML
```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: nginx-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: nginx
  minReplicas: 2
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 50
```

## Commands
```bash
# Create HPA
kubectl apply -f hpa.yaml

# Get HPA
kubectl get hpa

# Create HPA using command
kubectl autoscale deployment nginx --min=2 --max=10 --cpu-percent=50

# Watch HPA
kubectl get hpa -w
```

## Scaling Behavior
- cooldown period prevents rapid scaling
- Scale up is faster than scale down
- Default check interval: 15 seconds
