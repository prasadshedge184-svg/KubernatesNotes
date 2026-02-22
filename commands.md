### ✅ 1. Create a Pod using `kubectl run` 
```bash
kubectl run apple \
  --image=nginx \
  --restart=Never \
  --port=80 \
  --env="ENV=production" \
  --labels="app=fruit,team=dev" \
  --limits='cpu=1,memory=512Mi' \
  --requests='cpu=0.5,memory=256Mi' \
  -n fruits \
  --tty --stdin
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
### 🔍 Verify Pod Creation
```bash
kubectl get pods
```

