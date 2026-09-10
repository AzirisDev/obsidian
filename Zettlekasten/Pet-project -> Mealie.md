https://github.com/mealie-recipes/mealie/

We created namespace `tamak`. We will create deployment in this namescape and inside we will create container for mealie, cause mealie also has github container registry stuff.

Also we expose the port for container `9000` then forward `localhost:9000` to this port. In the end, we will see the application on our localhost.
	`kubectl port-forward pods/mealie-ndsgjsfjesfkes 9000`

Detailed yaml files are here: https://github.com/AzirisDev/lab/tree/master/kubernetes-fundamentals/namespaces

Links:

202609101236

