To create a pod in Kubernetes, you can use either a YAML file or a direct `kubectl` command.

### ✅ 1. Create a Pod using `kubectl run` (Quick Method)

```bash
kubectl run my-pod --image=nginx --restart=Never
```

* `my-pod` → Pod name
* `--image=nginx` → Container image
* `--restart=Never` → Ensures it creates a Pod (not a Deployment)
---

### ✅ 2. Create a Pod using a YAML file (Recommended)

Create a file called `pod.yaml`:

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

Then apply it:

```bash
kubectl apply -f pod.yaml
```

---

### 🔍 Verify Pod Creation

```bash
kubectl get pods
```

