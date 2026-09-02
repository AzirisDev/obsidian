Containers usually configured via environment variables:
- Directly setting up the variables is not recommended
```
docker run -d \
  --name mydb \
  -e POSTGRES_PASSWORD=secretpassword \
  -e POSTGRES_USER=myuser \
  -e POSTGRES_DB=myapp \
  postgres
```
- Use environment files instead:
```
# Create .env file
echo "POSTGRES_PASSWORD=secret" > db.env
echo "POSTGRES_USER=myuser" >> db.env

# Use it
docker run -d --env-file db.env postgres
```

Links:

202609011657

