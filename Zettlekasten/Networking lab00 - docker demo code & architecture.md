```
# Run two containers and inspect the components
docker run -d --name c1 alpine sleep 3600
docker run -d --name c2 alpine sleep 3600

# On the host: find veth pairs and the bridge
ip link show
ip link show master docker0

# Inside the container: see the other end
docker exec c1 ip addr
docker exec c1 ip route

# Docker's view
docker network inspect bridge
```
To identify `veth pair` we can look into `6: vetha08d257@if2` and match it with `eth0@if6` from container.

Here is architecture of above model:
![[Screenshot 2026-09-22 at 13.33.02.png|461]]

Links:

202609221302

