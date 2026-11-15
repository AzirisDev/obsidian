During installation of [[Installing K3S]], it already put into cluster `traefik service`. We can find it by `kubectl get svc -A`.

`traefik  LoadBalancer   10.43.250.236   192.168.1.154   80:32547/TCP,443:31517/TCP     4d1h`
It has external IP of machine where LoadBalancer itself is running. And it exposes ports `80, 443`.

#### Ingress configuration steps for application via yaml file

This will allow us to access anything from url but within local network.
1) Create `ingress.yaml` file in `../staging`:
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: linkding
spec:
  ingressClassName: traefik
  rules:
    - host: ldingress.azimsattykov.net
      http:
        paths:
          - backend:
              service:
	            # It is pointing to the service with name 'linkding'
	            # on port 9090
                name: linkding
                port:
                  number: 9090
            path: /
            pathType: Prefix
```
We get `ingressClassName` from following:
```
kubectl get ingressclasses.networking.k8s.io 

NAME                CONTROLLER                      PARAMETERS   AGE

traefik (default)   traefik.io/ingress-controller   <none>       4d2h
```
2) Check ingress by `kubectl get ingress`
3) Do `nskoolup ldingress.azimsattykov.net` for check local DNS - it will not find it. Because local DNS which is in `/etc/resolv.conf` does not contain information about that url
4) So we can add this record to the `hosts` file:
```
sudo vim /etc/hosts

192.168.1.154 ldingress.azimsattykov.net
```
Now check it

OR
3) We can add DNS record to `cloudflare`, with same url and IP address. It will switch off the proxy and be `http`. But now we can access `linkding` with any hosts changes.


Now lets try to configure ingress for `helm charts`. [[Ingress with Traefik for Helm charts]]


Links:

202611130952

