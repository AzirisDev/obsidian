Each instruction in Dockerfile creates a layer. Each layer is cached. Docker uses cached layers until lower layer is not changed.

`Order your Dockerfile from least frequently changed to most frequently changed.`

You can see the layers via `docker history myapp:1.0.0`

Links:

202609021508

