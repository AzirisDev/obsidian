- `kubectl exec -it nginx-docs -- /bin/bash` - run commands and enter the container inside pod
- `kubectl delete pod nginx-docs` - delete the pod
- inside the container you can ping other pod by their IP address
- `kubectl exec -it nginx-docs -c <container-name> -- /bin/bash` - run commands in certain container in pod

Links:

202609082054

 