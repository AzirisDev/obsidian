We run two containers via docker compose. We can see here that `docker compose` creates its own bridge separate from `docker-0`.

```
1. Look at the provided `compose.yaml` in this directory.
2. Start the stack:
    docker compose up -d
3. List Docker networks and find the one Compose created:
    docker network ls
4. Inspect the Compose network:
    docker network inspect lab00_default
5. Find the Linux bridge backing the Compose network:
    ip link show type bridge

    You should see a new bridge in addition to `docker0`.
6. Test that containers can reach each other by name:
    docker compose exec client ping -c 2 web
7. Verify with `ip link show master <bridge-name>` to see the veth pairs -- same primitives as docker0.
```



Links:

202609221646

