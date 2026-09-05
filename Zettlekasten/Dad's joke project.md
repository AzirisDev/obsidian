https://github.com/AzirisDev/lab/tree/master/containers/joke-dashboard
See codes by this link.

We have following structure in the directory:
```
joke-dashboard/
├── docker-compose.yaml
├── Dockerfile.updater
└── updater
```

It is not required to add `.updater` extension to Dockerfile. It is just convenient to refer in docker compose file to it. Same with `docker-compose.yaml`. Tool will search for default values anyway. We can run it like this `docker compose -f updater-compose.yml up -d` explicitly showing which file to run.

#### Docker compose commands
- `docker compose up -d` - run both containers
- `docker compose logs -f` - show logs in real time
- `docker compose ps` - check running containers
- `docker compose down` - stop everything
- `docker compose down -v` - stop everything and delete volume
- `docker compose up -d --build` - rebuild after changes
- `docker compose logs -f updater` - show logs for certain service
- `docker compose exec updater` - run command in service

Links:

202609051313

