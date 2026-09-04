- `docker build -t myapp .` - simple build
- `docker build -t myapp:1.0.0 .` - build with tag
- `docker build -t myapp:1.0.0 -t myapp:latest .` - multiple tags
- `docker build -f Dockerfile.prod -t myapp:prod .` - with Dockerfile location
- `docker build --no-cache -t myapp .` - force to rebuild all layers

##### Tagging 
- Use X.Y.Z, where:
	- X - major changes
	- Y - minor changes
	- Z - little patch
- `docker build -t myapp:$(git rev-parse --short HEAD) .` - git commit hash as tag
##### Tagging for pushing to registry
```
# For Docker Hub
docker build -t username/myapp:1.0.0 .

# For other registries
docker build -t ghcr.io/username/myapp:1.0.0 .
docker build -t registry.example.com/myapp:1.0.0 .
```

Links:

202609021513

