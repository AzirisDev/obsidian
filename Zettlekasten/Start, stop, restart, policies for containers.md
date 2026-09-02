1) `docker stop mycontainer`
	- SIGTERM sent
	- waits 10 seconds, or how much it was configured via `-t`
	- then send SIGKILL
2) `docker kill mycontainer`
	- SIGKILL sent
3) `docker restart mycontainer`
	- stop and start the container
	- data persists

There are several options for `restart-policy`:
- `no` - Never restart (default)
- `on-failure` - Restart only if exit code is non-zero
- `on-failure:3` - Restart on failure, max 3 attempts -> one-time workers
- `always` - Always restart, including on daemon start -> databases
- `unless-stopped` - Like always, but not if manually stopped -> servers

Ways to set/update restart policy:
- `docker run -d --restart=always nginx`
- `docker update --restart=always mycontainer`

Links:

202609012017

