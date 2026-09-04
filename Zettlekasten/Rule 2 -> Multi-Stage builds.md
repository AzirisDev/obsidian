Multi-Stage builds separates dependency build-time from run-time. So images become smaller and more secure. Only last stage becomes the actual image.
```
# Stage 1: Build
FROM ubuntu:24.04 AS builder
# ... install build tools, generate files ...

# Stage 2: Runtime
FROM nginx:1.28
COPY --from=builder /build/output /usr/share/nginx/html
```

For example here, the final image only contains nginx and the generated HTML - no bash, no build script.
Many DevOps tools (kubectl, docker, terraform) use multi-stage builds with Go to produce tiny images. The same principle applies: separate what you need to **build** from what you need to **run**.

Links:

202609041556

