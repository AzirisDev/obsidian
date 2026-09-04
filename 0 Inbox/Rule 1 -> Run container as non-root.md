We need to search for images without default root user. There are several options:
1) Find unprivileged images: 
```
FROM nginxinc/nginx-unprivileged:1.28

# Already runs as non-root (UID 101)
```
2) Change user in custom images:
```
FROM ubuntu:24.04

RUN apt-get update && apt-get install -y nginx && \
    rm -rf /var/lib/apt/lists/*

# Create non-root user
RUN useradd --create-home appuser

# Switch to non-root user
USER appuser

CMD ["nginx", "-g", "daemon off;"]
```


Links:

202609041545

