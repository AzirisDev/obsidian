`docker inspect mycontainer` - it will give you full information about the container.
you can use it with flag `-f '{{.State.Status}}` and retrieve certain information only.

`docker stats` - gives resources usage information of container
`docker stats --no-stream` - gives snapshot of that information for the moment of time

Links:

202609012022

