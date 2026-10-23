Dev Container Features are self-contained, shareable installation code and configs. 

We can configure it using command `Configure Container Features` or by changing this part in json:

```
"features": {
	"ghcr.io/devcontainers/features/azure-cli:1": {},
	"ghcr.io/flexwie/devcontainer-features/op:1": {}
}
```

Features might be like `Azure CLI, 1Password CLI` etc. 

#### Environment variables

We can also set environment variables like this:
```
"remoteEnv": {
	"My Variable": "Azim"
}
```
Rebuild the container and if you do:
	`env | grep My`
It will show our configured environment variable.


We can create our own features, but also we can use already created ones.

Links:

202610232223

