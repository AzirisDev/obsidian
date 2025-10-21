Dev containers - prefigured setup that lives inside isolated space.
- `sudo pacman -Syu docker` and enable & start that service.
- add user to docker group

Now we need DevPod - tool to create reproducible developer containers.
- `yay devpod`
- create symlink to easy usage: `ln -sf /usr/bin/devpod-cli /usr/bin/devpod`
-  `devpod ide none` - usually we start it with VsCode or Jetbrains
-   `devpod provider add docker`

We setup the devpod. Now we move to dev container json file. It is configuration file.
```
{
	"image": "mcr.microsoft.com/devcontainers/base:debian",
	"features": {
		"${any dev container feature reference}": {}
	},
	"settings": {
		"terminal.integrated.defaultProfile.linux": "zsh",
		"terminal.integrated.profiles.linux": {
			"zsh": {
				"path": "/bin/zsh"
			}
		}
	}
}
```
We can start dev container by `devpod up .` , being inside the project. 
 - `devpod ls` - shows running containers
 - `devpod ssh` - enter the dev container
Links:

202510201823

