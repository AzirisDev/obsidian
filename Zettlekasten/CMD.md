The command to run when a container starts.

```
# Exec form (preferred)
CMD ["./start"]

# Shell form
CMD ./start
```

Can be overridden at runtime:

```
docker run myapp ./other-script
```

Links:

202609021458

