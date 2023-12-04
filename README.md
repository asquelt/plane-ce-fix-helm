### Plane Helm Setup
---
## PROJECT FORKED FROM https://artifacthub.io/packages/helm/makeplane/plane-ce
# plane

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v0.12.2-dev](https://img.shields.io/badge/AppVersion-v0.12.2--dev-informational?style=flat-square)

🔥🔥🔥 Open Source JIRA, Linear and Height Alternative. Plane helps you track your issues, epics, and product roadmaps in the simplest way possible.

**Homepage:** <https://plane.so/>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| csansone | <ciro99678@gmail.com> | <https://github.com/Ciro99678> |

## Source Code

* <https://github.com/makeplane/plane>

Basic Install
```
helm install \
    --create-namespace \
    --namespace plane-ns \
    --set ingress.host="plane.example.com" \
    my-plane makeplane/plane-ce
```

Customise Remote Postgress URL
```
    --set postgres.local_setup=false \
    --set env.pgdb_remote_url="postgress://[username]:[password]@[pg-host]/[db-name]" \
```

Customise Remote Redis URL
```
    --set redis.local_setup=false \
    --set env.remote_redis_url="redis://[redis-host]:[6379]" \
```


Customise SMTP using 
```
    --set smtp.host="smtp.example.com" \
    --set smtp.user="my-email-address@example.com" \
    --set smtp.password="my-password" \
    --set smtp.from="Plane Mailer <mailer@example.com>" \
    --set smtp.port=587 \
    --set smtp.use_tls=1 \

```

Customise with SSL

_Before proceeding with SSL configuration, make sure you have followed the steps in "**SSL Certificate**" tab_
```
    --set ssl.createIssuer=true \
    --set ssl.issuer=cloudflare \
    --set ssl.token=xxxxxxxx \
    --set ssl.server="https://acme-v02.api.letsencrypt.org/directory" \
    --set ssl.email="plane-admin@example.com" \
    --set ssl.generateCerts=true \

```

### Cert-Manager Setup
---


If you are looking at generating Let's Encrypt SSL Certificate, preinstall Cert-Manager using below steps before moving to installing **Plane**
```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.13.1/cert-manager.crds.yaml

helm repo add jetstack https://charts.jetstack.io

helm install cert-manager --create-namespace --namespace cert-manager --version v1.13.1 jetstack/cert-manager --set startupapicheck.timeout=5m

helm uninstall cert-manager -n cert-manager

```
