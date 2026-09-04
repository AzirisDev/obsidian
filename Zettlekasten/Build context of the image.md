Docker send `build context`, when we build the container:
	`docker build -t myapp .   ---> build context is current directory`

That is why we need `.dockerignore` file:
```
# .dockerignore
.git/
*.log
.env
Dockerfile
.dockerignore
*.swp
*~
```

It save use from accidentally pass the secret files, env files, builds are smaller and faster.

Links:

202609021510

