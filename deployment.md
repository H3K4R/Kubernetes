🚀 Kubernetes Deployment — Complete Explanation

A Deployment in Kubernetes is a controller that manages a set of identical Pods.
It ensures the desired state of your application (number of pods, container image, version) is always maintained.

You usually never create Pods manually — instead, you create a Deployment, and the deployment creates and manages pods for you.

📘 Why Deployment Is Used?
✅ 1. Creates and Manages Pods Automatically

You define:

container image

number of replicas

labels

ports

Deployment will create Pods based on this template.

✅ 2. Self-Healing

If a Pod crashes or a node goes down:

Deployment automatically creates a new Pod.

✅ 3. Rolling Updates

You can update:

container image

environment variables

configuration

Kubernetes will replace old Pods with new Pods gradually — without downtime.

✅ 4. Rollbacks

If something goes wrong after an update:

kubectl rollout undo deployment <name>


Deployment can instantly roll back to the previous version.

✅ 5. Scaling

Increase or decrease replicas at any time.

kubectl scale deployment nginx-deploy --replicas=5


Kubernetes will add or remove Pods.

✅ 6. Declarative Configuration

Everything is defined in YAML — easy for GitOps, CI/CD, version control.

🔹 Summary (for interview)

“A Deployment ensures your application runs in the desired number of identical Pods, provides rolling updates, rollbacks, scaling, self-healing, and declarative configuration.”

📄 Structure of a Deployment YAML
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


➡️ Deployment → creates Pods
➡️ Pods → run containers

🔥 Important Deployment Features (Must Know)
Feature	Explanation
Replica Management	Keeps desired number of Pods running
Self-healing	Restarts Pods if they fail
Rolling Updates	Update app version without downtime
Rollbacks	Revert bad deployments
Scaling	Increase/decrease number of Pods
Declarative	YAML-based configuration
Label Selector	Controls which Pods belong to this Deployment
🧪 Useful Deployment Commands
▶️ 1. Create deployment
kubectl apply -f deployment.yaml

▶️ 2. List deployments
kubectl get deployments

▶️ 3. Describe a deployment
kubectl describe deployment nginx-deployment

▶️ 4. Check rollout status
kubectl rollout status deployment nginx-deployment

▶️ 5. Update the image (rolling update)
kubectl set image deployment/nginx-deployment nginx=nginx:1.27

▶️ 6. Rollback to previous version
kubectl rollout undo deployment nginx-deployment

▶️ 7. View rollout history
kubectl rollout history deployment nginx-deployment

▶️ 8. Scale deployment
kubectl scale deployment nginx-deployment --replicas=5

▶️ 9. Delete deployment
kubectl delete deployment nginx-deployment


🔥 Quick One-Line Definition (Best for Interview)

"A Deployment is a Kubernetes controller that manages ReplicaSets and Pods, enabling rolling updates, rollbacks, scaling, and self-healing of applications."