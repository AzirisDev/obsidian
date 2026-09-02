```
                    ┌──────────┐
         create     │ Created  │
        ─────────►  └────┬─────┘
                         │ start
                         ▼
┌─────────┐ stop    ┌──────────┐ pause   ┌──────────┐
│ Exited  │◄────────│ Running  │────────►│ Paused   │
└─────────┘         └──────────┘◄────────└──────────┘
     ▲                   │        unpause
     │                   │ (process exits)
     └───────────────────┘
```

Here are state of container. We can check it with `docker ps -a`.

Links:

202609012004

