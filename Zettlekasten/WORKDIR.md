Sets the working directory for subsequent instructions.

```
WORKDIR /app

# Now these happen in /app
COPY . .
RUN chmod +x start
CMD ["./start"]
```

Links:

202609021456

