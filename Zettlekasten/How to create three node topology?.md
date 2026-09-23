Yaml file is pretty much the same. You just add more nodes.

>Important things to mention: `endpoints` should contain only one pair of connection
>Example:
>`- endpoint: ["srl1:e1-1", "srl2:e1-1"]
>`- endpoint: ["srl2:e1-2", "srl3:e1-2"]`

>If you want to kill the process, run `Ctrl+Shift+C`.


#### Generate the documentation
```
1. With your three-node lab running, generate the graph:
    clab graph -t three-node.clab.yml --drawio
2. Also try the inspect output in different formats:
    clab inspect -t three-node.clab.yml --format json > lab-info.json
```

Links:

202609231237

