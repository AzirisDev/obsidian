It is API object in k8s cluster that manages HTTP/HTTPS access to services inside.
One ingress can expose externally many services.

```
                                        ┌─► api-service
                                        │
  ONE Cloud LB ──► Ingress Controller ──┼─► frontend-service
  ($, one IP)                           │
                                        ├─► auth-service
                                        │ 
                                        ├─► admin-service
                                        │
                                        └─► ... all 10 ...
```

One Cloud LB. One IP. One bill. The controller reads the `Host` header and splits traffic to the right service internally. Adding an 11th service = just add a routing rule, no new infrastructure.

**That's the whole point.** Ingress is a shared front door so you don't buy a separate front door for every room.

Links:

202609111626

