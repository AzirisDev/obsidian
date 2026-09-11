Services in k8s offers stable network abstraction to expose consistent endpoint to set of pods.
It uses `label selector` to target desired set of pods.

There are several types of `Services`:
- `Cluster IP` - default one; it exposes internal virtual IP -> necessary for communication within cluster like DB is talking to frontend.
- `NodePort` - each node get specific port -> External traffic can hit `NodeIP:NodePort` and get to Service. It is not recommended on production
- `LoadBalancer` - used for cloud providers; routes external traffic to services. Using this, we are free from doing port forwarding to handle requests.


Commands:
- `kubectl get services`
- `kubectl expose pod/deployment/service frontend --port 8080` -   create new service with selector `frontend` -> this should match with the label of our `deployment`

Links:

202609111241

