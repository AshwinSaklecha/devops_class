# Deep Dive into Kubernetes Services

## Service Discovery
- K8s provides built-in DNS
- Services can be accessed by name
- Format: `<service-name>.<namespace>.svc.cluster.local`

## Endpoints
- Services don't connect to pods directly
- Uses Endpoints object to track pod IPs
- Endpoints updated when pods change

## Service vs Ingress
- Service exposes single service
- Ingress provides HTTP routing for multiple services
- Ingress handles SSL termination

## NodePort Deep Dive
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nodeport-service
spec:
  type: NodePort
  selector:
    app: myapp
  ports:
  - port: 80
    targetPort: 8080
    nodePort: 30080
```
- nodePort: port on node (30000-32767)
- port: service port
- targetPort: pod port

## LoadBalancer Example
```yaml
apiVersion: v1
kind: Service
metadata:
  name: lb-service
spec:
  type: LoadBalancer
  selector:
    app: myapp
  ports:
  - port: 80
    targetPort: 8080
```

## Headless Services
- Set clusterIP: None
- Returns pod IPs directly
- Used for stateful applications
