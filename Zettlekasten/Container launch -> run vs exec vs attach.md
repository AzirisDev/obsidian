1) `docker run -it ubuntu bash`
	- it creates a new container, every time
	- starts container with command 
2) `docker exec -it mycontainer bash`
	- runs command on already `running` container
	- starts a new process
3) `docker attach mycontainer`
	- connects to the main PID
	- share same STDIN/STDOUT
	- `Dangerous!!!`: Ctrl+C will stop the container

Links:

202609012005

