# Experiment 12: Study and Analyse Container Orchestration using Kubernetes

## Objective
Learn the basic Kubernetes building blocks and how deployments, services, scaling, and self-healing work.

## Why Kubernetes
Kubernetes is the industry standard for container orchestration because it provides advanced scheduling, scaling, and ecosystem support.

## Core Concepts
| Docker Concept | Kubernetes Equivalent | Meaning |
|---|---|---|
| Container | Pod | Smallest deployable unit |
| Compose service | Deployment | Declares desired application state |
| Load balancing | Service | Exposes pods reliably |
| Scaling | ReplicaSet | Keeps the required number of pods running |

## Hands-On Lab
### 1. Create a deployment
Create `wordpress-deployment.yaml`:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wordpress
spec:
  replicas: 2
  selector:
    matchLabels:
      app: wordpress
  template:
    metadata:
      labels:
        app: wordpress
    spec:
      containers:
      - name: wordpress
        image: wordpress:latest
        ports:
        - containerPort: 80
```

Apply it:
```bash
kubectl apply -f wordpress-deployment.yaml
kubectl get pods
```

### 2. Expose it as a service
Create `wordpress-service.yaml`:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: wordpress-service
spec:
  type: NodePort
  selector:
    app: wordpress
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30007
```

Apply it:
```bash
kubectl apply -f wordpress-service.yaml
kubectl get svc
```

Open the app:
```text
http://<node-ip>:30007
```

### 3. Scale the deployment
```bash
kubectl scale deployment wordpress --replicas=4
kubectl get pods
```

### 4. Test self-healing
```bash
kubectl delete pod <pod-name>
kubectl get pods
```

## Swarm vs Kubernetes
| Feature | Docker Swarm | Kubernetes |
|---|---|---|
| Setup | Easier | More complex |
| Scaling | Basic | Advanced |
| Ecosystem | Smaller | Very large |
| Industry use | Less common | Standard |

## Real Cluster Notes
For a real cluster, `kubeadm` is used to install the control plane and join worker nodes.

## Result
Kubernetes manages desired state through deployments and services, automatically keeping your application available and scalable.
