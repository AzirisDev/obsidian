DevPod is open-source client solution to run Dev Containers. We can pass here our dotfiles (custom configurations of our work environment.)

It has Providers. Providers determine how and where your workspaces run. It can be Docker, Kubernetes, SSH, AWS, Azure, etc.

Commands that we use:
- `devpod up . --ide none --dotfiles git:github.com:AzirisDev/dotfiles` - running the dev container from working folder
- `devpod ls` - see all dev containers
- `devpod ssh ...` - ssh into one of the dev container 

It goes over routine for finding common executable scripts and runs it.


#### Defaults
- `devpod ide use none` - sets default ide to none
- `devpod ide list` - list of all ide-s 
- `devpod context set-options -o DOTFILES_URL=git@github.com:AzirisDev/dotfiles.git` - set default dotfiles pass to dev containers

#### DevPods in ARM and AMD architecture
You should be aware that devpod might work on Linux machines but crash on MacOS machines due to incompatibility of package managers or other stuff.
Links:

202610232305

