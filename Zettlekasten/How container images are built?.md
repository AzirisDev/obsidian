Images are built in layers. Many containers share base, ordinarily downloaded layers.
Only differences are stored per container.

Blog post about container layers
[https://www.grant.pizza/blog/overlayfs/](https://www.grant.pizza/blog/overlayfs/ "https://www.grant.pizza/blog/overlayfs/")

```
┌─────────────────────────────────┐
│   Container Layer (read-write)  │  ← Your changes at runtime
├─────────────────────────────────┤
│   App Code Layer (read-only)    │
├─────────────────────────────────┤
│   Dependencies Layer (read-only)│
├─────────────────────────────────┤
│   Base Image Layer (read-only)  │
└─────────────────────────────────┘
```

When you, for example, edit file from lower layer, it creates copy of it and put it in upper layer.
If you try to delete the file from lower layer, it will create whiteout file -> make that file as deleted/non-existent for upper layer.

Links:

202608312217

