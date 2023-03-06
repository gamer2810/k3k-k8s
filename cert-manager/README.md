# CERT-MANAGER

# INTENTION
Automatic HTTPS certificate renewal, managing...
# STEPS
Run

```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.11.0/cert-manager.yaml FIRST
```

Follow [Cloudflare setup](https://cert-manager.io/docs/configuration/acme/dns01/cloudflare/)

Included are sample config files