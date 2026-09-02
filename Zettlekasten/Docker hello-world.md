After successful installation, run `docker run hello-world`.
It will do following:
- Search for local image -> did not find
- Pull from Docker hub -> it is public registry where we have many images
- Create and start container from that image

We can search for images from hub using:
	 `docker search nginx`
We can pull that image:
	`docker pull nginx` - will fetch the latest
	`docker pull nginx:1.28` - will fetch image with 1.28 tag
	`docker pull nginx:1.28-alpine` - will fetch image with 1.28-alpine variant
To see all images:
	`docker images`

Links:

202609011638

