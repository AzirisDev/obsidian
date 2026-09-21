https://linkding.link

It is self-hosted bookmark application. We will install it first via `docker-compose`. Then convert it to `k8s` setup.

#### Docker compose setup

Download via `curl -L -O` docker compose yaml file and .env file.
Create `data` folder to mount here the volume.
Run `docker-compose up -d`.
Use [[local SSH port forwarding tunnel]] to open app in host device.
Run this to create user:
	`docker-compose exec linkding python manage.py createsuperuser --username=azim --email=azim@example.com` 

#### K8s setup

Create `namespace.yaml` and apply it.
Create `persistentVolumeClaim` and apply it. The name here should match the name in the deployment yaml file.
Create `secrets` file and apply it. Secrets are k8s objects that can store simple and secure data like .env file.
Create deployment yaml file.
Create service with type `LoadBalancer` to reach out the app via localhost.


#### Things that I learned
- `apiVersion` of different k8s objects are different. For example, deployment is `apps/v1`; secrets, namespaces, persistent volume claims are just `v1`
- We can port forward a pod via k9s. Then us [[local SSH port forwarding tunnel]] on work station and open same app here.
- If you do port-forwarding via k9s, it dies with it.
- ```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: linkding        # <- Service does NOT look at this
  namespace: linkding
spec:
  replicas: 1
  selector:
    matchLabels: { app: linkding } # <- Deployment uses this to find its own Pods
  template:
    metadata:
      labels: { app: linkding } # <- THIS is what the Service selector matches
    spec:
      containers:
        - name: linkding
          image: sissbruecker/linkding:latest
          ports:
            - containerPort: 9090
          envFrom:
            - secretRef: { name: linkding-admin }
          volumeMounts:
            - name: data
              mountPath: /etc/linkding/data
          readinessProbe:
            httpGet: { path: /health, port: 9090 }
            initialDelaySeconds: 10
      volumes:
        - name: data
          persistentVolumeClaim:
            claimName: linkding-data
  ```
- probes - `readinessProbe` and `livenessProbe`. Readiness gates traffic (fail → pulled from Service endpoints, no restart). Liveness gates restarts (fail → kubelet kills and restarts the container).

Links:

202609210917

