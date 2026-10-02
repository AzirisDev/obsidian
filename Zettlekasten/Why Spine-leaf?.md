In production, we can not have just mesh where every router is connected with each other like in [[Dynamic Routing & BGP]]. First iteration was 3-tier model: core, distribution and access layers. It solved physical scale problem and worked with Spanning Tree Protocol to prevent loops. But it leads to many redundant, unused links.

Then Charles Clos drops telephone switching paper in 1953 that solved both problems. Clos spine-leaf architecture keeps all links active and load-balance across all network with [[ECMP]]. And scaling happens independently.

Links:

202610011144

