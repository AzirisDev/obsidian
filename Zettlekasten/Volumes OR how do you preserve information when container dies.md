Recipe for creating volumes and create containers that never lost its information:
- `docker create volume mydata`
- ```
docker run -d \
  --name mybox \
  -v mydata:/data \
  alpine sleep 3600 ---> create container and mount volume to /data
```
- `docker exec mybox sh -c "echo 'important data' > /data/myfile.txt"`
- ```
docker rm -f mybox
docker run -d \
  --name mybox \
  -v mydata:/data \
  alpine sleep 3600 ---> remove and recreate the container
```
- `docker exec mybox cat /data/myfile.txt   ---> data is still there`


Here are other volume commands:
```
# List volumes
docker volume ls

# Inspect a volume
docker volume inspect mydata

# Remove a volume
docker volume rm mydata

# Remove unused volumes
docker volume prune
```

Links:

202609012024

