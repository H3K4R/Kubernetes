# 🚀 Kubernetes Deployment — Complete Explanation

A **Deployment** in Kubernetes is a controller that manages ReplicaSets and Pods.  
It ensures your application always runs in the desired state (number of pods, image version, etc.).

You **never** create pods manually — you create a Deployment, and it manages pods for you.

---

## 📘 Why Deployment Is Used?

### ✅ 1. Creates and Manages Pods Automatically  
You define:

- container image  
- replicas  
- labels  
- ports  

The Deployment creates Pods from this template.

---

### ✅ 2. Self-Healing  
If a Pod crashes or a node goes down →  
Kubernetes automatically creates a new one.

---

### ✅ 3. Rolling Updates  
You can update:

- image  
- environment variables  
- configuration  

Kubernetes rolls out new Pods **without downtime**.

---

### ✅ 4. Rollbacks  

```bash
kubectl rollout undo deployment <name>
```

Reverts to the previous stable version.

---

### ✅ 5. Scaling  

```bash
kubectl scale deployment nginx-deployment --replicas=5
```

Increase or decrease pod count anytime.

---

### ✅ 6. Declarative Configuration  
Everything is defined in YAML → good for CI/CD & GitOps.

---

## 🔹 Summary (Interview Answer)

> **“A Deployment ensures your application runs in the desired number of identical Pods, supports rolling updates, rollbacks, scaling, self-healing, and declarative configuration.”**

---

# 📄 Deployment YAML Example

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
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
          ports:
            - containerPort: 80
```

---

# 🔥 Important Deployment Features (Must Know)

| Feature | Explanation |
|--------|-------------|
| Replica Management | Ensures desired number of pods |
| Self-Healing | Recreates failed pods |
| Rolling Updates | Zero-downtime updates |
| Rollbacks | Revert to previous version |
| Scaling | Increase/decrease pods |
| Declarative | Entire config in YAML |
| Label Selector | Selects pods managed by Deployment |

---

# 🧪 Useful Deployment Commands

### ▶️ 1. Create deployment
```bash
kubectl apply -f deployment.yaml
```

### ▶️ 2. List deployments
```bash
kubectl get deployments
```

### ▶️ 3. Describe a deployment
```bash
kubectl describe deployment nginx-deployment
```

### ▶️ 4. Check rollout status
```bash
kubectl rollout status deployment nginx-deployment
```

### ▶️ 5. Update image (Rolling Update)
```bash
kubectl set image deployment/nginx-deployment nginx=nginx:1.27
```

### ▶️ 6. Rollback
```bash
kubectl rollout undo deployment nginx-deployment
```

### ▶️ 7. View rollout history
```bash
kubectl rollout history deployment nginx-deployment
```

### ▶️ 8. Scale deployment
```bash
kubectl scale deployment nginx-deployment --replicas=5
```

### ▶️ 9. Delete deployment
```bash
kubectl delete deployment nginx-deployment
```

---

# 🔥 One-Line Interview Definition

> **“A Deployment is a Kubernetes controller that manages ReplicaSets and Pods, enabling rolling updates, rollbacks, scaling, and self-healing.”**
