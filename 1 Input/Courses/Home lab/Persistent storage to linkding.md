Create `PersistentVolumeClaim` resource and link it to deployment like in [[Persistent storage]].
Do not forget to mention it in `kustomization.yaml` for flux to reconcile it and apply.

`linkding` has its own python file to create super user:
`kubectl exec -it -n linkding linkding-7bffb6cdb9-h7mnm -- python manage.py createsuperuser --username=azim --email=azim@example.com`

Now all data is stored in volume resource and pod deletion is not affecting it.

But now we have another problem with security -> we are entering pods as a root user
It is fixed by [[Security context for deployment]]


Links:

202611110956

