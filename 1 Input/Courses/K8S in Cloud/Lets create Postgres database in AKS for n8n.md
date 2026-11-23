n8n self-hosting application by default creates SQLite database in `/home/node/.n8n/database.sqlite`. It sits in our [[Persistent storage]], which is in Azure Disk. So when we delete the resources and create them back, we have different external IP, new, fresh storage and data. It might work in homelab but it is a problem in Production:
- You can't scale - storage is per node
- Your app's state is locked inside one pod's disk.

According to documentation we need to add to the `configmap.yaml` following:
```
...
DB_TYPE: "postgresdb"
# this one we get from host in Azure resource Endpoint field
DB_POSTGRESDB_HOST: "psql-n8n-mercury.postgres.database.azure.com"
DB_POSTGRESDB_PORT: "5432"
DB_POSTGRESDB_DATABASE: "n8n"
DB_POSTGRESDB_USER: "n8nadmin"
DB_POSTGRESDB_PASSWORD: "n8n-password-123"
...
```

In terraform file, we have add resources:
https://github.com/AzirisDev/mercury-workflows/blob/main/phase-3-aks/main.tf

Links:

202611231455

