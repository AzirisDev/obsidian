`FROM` in Dockerfile means the base layer:
NEVER use `latest` tag.
Try to choose images based on the usage of the container.

We can also pass the arguments to Dockerfile and use them in `FROM`:
`ARG UBUNTU_VERSION=24.04`
`FROM ubuntu:${UBUNTU_VERSION}`
then run:
`docker build --build-arg UBUNTU_VERSION=22.04 -t myapp .`


Links:

202609021450

