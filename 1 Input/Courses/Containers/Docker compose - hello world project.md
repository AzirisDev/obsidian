Docker compose is a tool that can run containers on same host and talk to each other. It creates network for containers to talk. Our hello world project will be website that serve dad's joke every 30 seconds.
- `updater` - bash script container that fetches jokes
- `nginx` - serves generated html page
- `shared volume` - both containers access the same `/html` directory

Example of Docker compose file:
```
services:
  db:
    image: postgres:16
    volumes:
      - mydata:/var/lib/postgresql/data
  api:
    image: myapi:1.0.0
    environment:
      - DATABASE_URL=postgres://db/app
  web:
    image: nginx:1.28
    ports:
      - "80:80"

volumes:
  mydata:
```

[[Dad's joke project]]
[[Docker compose vs Kubernetes]]

Links:

202609051307

