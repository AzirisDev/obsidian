We need them to check whether our container is running. Cause container might be up, but not running.

```
FROM nginx:1.28

# Install curl for helth checks
RUN apt-get update && \
    apt-get install -y --no-install-recommends curl && \
    rm -rf /var/lib/apt/lists/*

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD curl -f http://localhost/ || exit 1

EXPOSE 80
```
#### **Options**
- `--interval`: Time between checks (default 30s)
- `--timeout`: Max time for check to complete
- `--start-period`: Grace period for startup
- `--retries`: Failures before marking unhealthy

Links:

202609041603

