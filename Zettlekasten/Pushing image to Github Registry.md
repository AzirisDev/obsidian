Github Registry works as Docker hub, allows store images.
1) Generate PAT with write and read packages permission
2) ```
# Store your token (don't commit this!)
export CR_PAT=fdafeaf

# Login
echo $CR_PAT | docker login ghcr.io -u YOUR_GITHUB_USERNAME --password-stdin
```

3) ```
# Tag your local image for ghcr.io
docker tag backup:1.0.0 ghcr.io/yourusername/backup:1.0.0

# Push to registry
docker push ghcr.io/yourusername/backup:1.0.0
```

4) ```
docker pull ghcr.io/yourusername/backup:1.0.0
docker build -t ghcr.io/yourusername/backup:1.0.0 .
docker push ghcr.io/yourusername/backup:1.0.0
```


Links:

202609021648

