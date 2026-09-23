Define a topology:
```
# lab.clab.yml
name: first-lab

topology:
  nodes:
    srl1:
      kind: srl
      image: ghcr.io/nokia/srlinux:24.10.1

    srl2:
      kind: srl
      image: ghcr.io/nokia/srlinux:24.10.1

  links:
    - endpoints: ["srl1:e1-1", "srl2:e1-1"]
```

- `clab deploy` - inside folder or `clab deploy -t topology/lab.clab.yml`
- `clab inspect` - to get the topology information
- `clab graph -t topology/lab.clab.yml` - will give you the links to browser to see topology
- `clab destroy -t topology/lab.clab.yml --cleanup` - remove and clean up the topology

Links:

202609230959

