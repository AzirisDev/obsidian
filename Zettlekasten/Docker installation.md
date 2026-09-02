You can go and find `Docker Engine` installation and run commands according to guideline.
You can also use the convenience script and run it, it will do all setup automatically:
	 `curl -fsSL https://get.docker.com -o get-docker.sh
	-`sudo sh ./get-docker.sh --dry-run`

Then it is important to add your user to `docker` group to avoid every rime running commands with `sudo`:
	`sudo usermod -aG docker $USER`

Verify installation with `docker version` or `docker info`.

Links:

202609011638

