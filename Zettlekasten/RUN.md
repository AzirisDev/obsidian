This gives instructions to run commands during build process.
We need to bundle dependencies, cause each `RUN` line creates separate layer.
```
RUN apt-get update && \
    apt-get install -y curl && \
    apt-get clean
```

Container starts empty, we need to include every dependency that it needs to run.

Links:

202609021453

