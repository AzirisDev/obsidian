We can run single command with `docker exec`:
- `docker exec mycontainer bash`
- `docker exec mycontainer sh`
- `docker exec mycontainer ps aux`  and etc.

We can run commands as different user:
- `docker exec -u root mycontainer whoami`
- `docker exec -u 1000 mycontainer id`

We can run commands with environment variables:
- `docker exec -e DEBUG=true mycontainer ./myscript`
- `docker exec --env-file .env mycontainer ./myscript`

Links:

202609012010

