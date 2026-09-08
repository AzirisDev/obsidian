```
# Get pods
kubectl get pods

# Get pods with more information like IP addresses
kubectl get pods -o wide

# Get pod's yaml file
kubectl get pod nginx -o yaml

# Edit pod's yaml file
kubectl edit pod nginx

# Run a single pod
kubectl run nginx --image=nginx

# Run and drop into an interactive shell, delete on exit
kubectl run tmp --image=busybox --rm -it --restart=Never -- sh

# Run with a specific command
kubectl run test --image=busybox --restart=Never -- echo "hello"

# Set env vars, ports, labels
kubectl run web --image=nginx --port=80 --env="ENV=prod" --labels="app=web"
```


Links:

202609081718

