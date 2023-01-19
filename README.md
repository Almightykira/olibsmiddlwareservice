## PORTAL

-   docker
-   kubernetes
-   gitlab-runner
-   gitlab
-   gitlab-registry

## Local deployment

```bash
minikube start \
-p digibank \
--cpus 2 \
--memory 2g \
--nodes 2 \
--driver virtualbox \
--insecure-registry=192.168.100.250:8086 \
--addons=metrics-server \
--addons=dashboard \
--addons=registry-creds \
--addons=metallb \
--addons=ingress \
--kubernetes-version=1.21.8 \
--feature-gates=HPAContainerMetrics=true

# set profile
minikube profile digibank

# configure credential for insecure registry
minikube addons configure registry-creds

## configure loadbalancer ip.
minikube addons configure metallb
```

### Ingress Controller

Because this project using ingress, edit your `/etc/hosts` then add domain `digibank` to your minikube cluster ip

```bash
$(minikube ip) digibank
```

## Environtment

-   review, for internal
