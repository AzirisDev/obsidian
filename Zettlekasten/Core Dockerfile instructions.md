[[FROM]] ubuntu:24.04
[[RUN]] apt-get update && apt-get install -y curl
[[COPY]] start /app/
[[WORKDIR]] /app
[[ENV]] APP_ENV=production
[[EXPOSE]] 8080
[[ENTRYPOINT]] `["./backup"]
[[CMD]] `["list"]`

Links:

202609021244

