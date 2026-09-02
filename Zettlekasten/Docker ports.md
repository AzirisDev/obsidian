To connect outside port to port inside container use following format: 
`-p HOST_PORT:CONTAINER_PORT`

- `docker run -d -p 8080:80 nginx`
	- `docker run -d -p 8080:80 -p 8343:43 nginx` - you can do multiple ports
- `docker run -d -p 80 nginx` - random port

Links:

202609011655

