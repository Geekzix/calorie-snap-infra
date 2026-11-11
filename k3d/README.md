Configuration	Reason
1 server	Kubernetes control plane
2 agents	Separate worker nodes
K3s v1.37.2	Matches your kubectl
Port 8088	HTTP entry point
Port 8448	HTTPS entry point
Disable Traefik	We'll install and configure NGINX Ingress ourselves

```bash
k3d cluster create --config k3d/k3d-infra-config.yaml

```
