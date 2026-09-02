Ways to run containers:
- `docker run nginx` - run container on foreground
- `docker run -d nginx` - run container in detached mode
- `docker run -d --name webserver nginx` - run container in detached mode with the name, otherwise it will give random name
- `docker run -it --rm ubuntu bash` - run container with interactive terminal in it
	- `-i` - keep STDIN open
	- `-t` - allocate pseudo-terminal
	- `--rm` - remove container when it exits
	- when you exit, containers stops

See containers:
- `docker ps` - running containers
- `docker ps -a` - all containers



Links:

202609011646

