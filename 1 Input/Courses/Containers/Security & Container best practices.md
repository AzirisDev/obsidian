Containers are isolated but they all share host kernel. So vulnerable container means vulnerable production. We need be careful with what goes INTO the container and how they RUN.

[[Rule 1 -> Run container as non-root]]
[[Rule 2 -> Multi-Stage builds]]
[[Rule 3 -> Choose base images wisely; try to always use minimal versions of images]]
[[Rule 4 -> Add Health Checks to the container]]


I faced some interesting thing called [[local SSH port forwarding tunnel]].
Links:

202609041505

