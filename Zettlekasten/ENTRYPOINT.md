It is like `CMD`, but harder to override. We have to use it when container runs specific executable 
-> `Container IS the command`
For example, backup container.

Create `backup`:

```
#!/bin/bash
case "$1" in
  create)  echo "Creating backup..." ;;
  restore) echo "Restoring from backup..." ;;
  list)    echo "Listing backups..." ;;
  *)       echo "Usage: backup {create|restore|list}" ;;
esac
```

Create `Dockerfile`:

```
FROM ubuntu:24.04

WORKDIR /app
COPY backup .
RUN chmod +x backup

ENTRYPOINT ["./backup"]
CMD ["list"]
```

```
docker build -t backup:1.0.0 .

docker run backup:1.0.0              # Runs: ./backup list
docker run backup:1.0.0 create       # Runs: ./backup create
docker run backup:1.0.0 restore      # Runs: ./backup restore
```


Links:

202609021458

