Pod is a smallest element running in k8s cluster.
It's name come from "pod of whales" - group of whales.

Usually pod is single containered, but it can be multi-container also init container.
It has its own networking and storage.

What is has inside:
- `Pod IP` - one IP shared within Pod
- `Volumes` - shared storage mounted into containers
- `Init containers` - setup that runs `before` app containers start
- `Restart policy`

It is something that will die and become alive, replaced with `Deployment`.

[[Imperative method to run pod]]
[[Declarative method to run pod -> yaml files]]
[[Interacting with pods]]

Links:

202609081705

