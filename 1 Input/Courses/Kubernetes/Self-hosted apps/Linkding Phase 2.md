#### What's new
Let's add `postgres` database into cluster and make our `linkding` deployment talk to it. Here we getting several new stuff:
- `StatefulSet` - the prod ready way to run database except using Deployment
- `Service DNS` - the way `linkding` finds `postgres` without IP
- `Depedency ordering` - `linkding` waits DB to be reachable

#### Architecture
```
┌─────────────┐         ┌──────────────────┐
│  linkding   │  ─────► │  Service:        │
│ (Deployment)│  :5432  │  postgres        │ ──► postgres-0 (StatefulSet pod)
└─────────────┘         │  (headless)      │        │
                        └──────────────────┘        └── PVC: data-postgres-0
        both read DB creds from the same Secret ◄────┘
```

#### [[Secret file and usage]]
#### [[Postgres - StatefulSet + Headless Service]]
#### [[Linkding - Deployment + init container]]


#### Things that I learned
- We can use `---` in yaml files and put several yaml content into one file.
- We can run `kubectl apply -f ./linkding/` and apply whole folder files

Links:

202609211540

