We can write yaml files ourselves. But usually we do not: get yaml from internet, use your old files, get from runner image.

#### Generate yaml files

`kubectl run nginx-yaml --image=nginx --dry-run=client -o yaml > nginx-pod.yaml`
- usually `run` command create pod named  `nginx-yaml` and add it to the cluster
- but `dry-run` command simulates it locally and `-o` outputs it's yaml file
- then we put the output into the file `nginx-pod.yaml`

- if we pass `server` to `dry-run`, for example, it will connect to API server and checks for validity to be added to cluster.

To create pod from yaml file:
- `kubectl create -f nginx-pod.yaml` - it only creates new pod and throws error if it already exists
- `kubectl apply -f nginx-pod.yaml` - it creates or applies changes to pod

#### Get yaml files from internet
```
Tricks:
1) In Kubernetes documentation, the fastest way to get to pods yaml file is to search for "apiver" -> cause each yaml has "apiVersion:" field

2) In vim, after copy and paste, you better enable paste mode -> :set paste
   then paste it. Good identation will persist
```



 

Links:

202609082009

