### ✅ 1. Create a Pod using `kubectl run` 
```bash
kubectl run my-pod --image=nginx --restart=Never
```
### ✅ 2. Create a Pod using a YAML file 
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: nginx
    ports:
    - containerPort: 80
```
```bash
kubectl apply -f pod.yaml
```
---
### 🔍 Verify Pod Creation
```bash
kubectl get pods
```

