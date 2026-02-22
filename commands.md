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

kubectl apply -f pod.yaml

kubectl get pods

kubectl get all -n fruits

```

