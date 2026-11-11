We were port-forwarding to access our linkding application. Now we want to access the app via internet from wherever.

We choose to use `Cloudflare` and get domain here. Why?

#### Why Cloudflare?
- Our machine needs a reachable public IP
- Our router must forward ports to the cluster's ingress
- Our exposed IP with port should be stable
- We need TLS certificate 
- We need our home IP expose directly, so anyone can scan, hack and attack it

Cloudflare solves all this problems. Its core products are global DNS, a reverse proxy, DDoS protection, automatic TLS certificates and, the most important tool, Cloudflare tunnel.

#### Cloudflare tunnel
We will run small agent `cloudflared` inside our cluster as Deployment. It creates `outbound connection` to the Cloudflare's edge. The flow of requests will look like this:
`User → app.yourdomain.com → Cloudflare edge → (existing outbound tunnel) → cloudflared pod → your Service / Ingress`

There are certain trade-offs like trusting third-party, vendor lock-in infrastructure, and restriction for high-load streaming stuff. But for our situation it is not relevant.

Also there are alternatives:
- Port forwarding + DDNS + cert-manager: doing everything by hand
- Tailscale: but you can use it only yourself

#### [[How to configure Cloudflare tunnel?]]


Links:

202611111535

