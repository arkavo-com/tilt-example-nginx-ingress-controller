# NGINX Ingress Controller 1.0 orchestrated via Tilt 0.22

Example project using NGINX Ingress Controller 
in a development Kubernetes cluster using Tilt.
Three namespaces for three services.  One namespace
for the ingress controller.  One host name, `localhost`,
with two paths and one default path.

References
- https://github.com/kubernetes/ingress-nginx
- https://github.com/tilt-dev/tilt

## Setup

Install Tilt  
https://docs.tilt.dev/install.html

Install ctlptl  
https://github.com/tilt-dev/ctlptl

Install KIND  
https://kind.sigs.k8s.io/docs/user/quick-start/

Setup KIND  
https://github.com/tilt-dev/kind-local  
https://github.com/tilt-dev/ctlptl#kind-with-a-built-in-registry-at-a-random-port  

Install NGINX Ingress Controller  
https://kubernetes.github.io/ingress-nginx/deploy/
```shell
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.0.0/deploy/static/provider/cloud/deploy.yaml
```

## Execute

`tilt up`

hit (space) to open the browser  
click links under `ingress-nginx-controller`

## Troubleshoot

NGINX Ingress Controller - Troubleshooting Common Issues  
https://docs.nginx.com/nginx-ingress-controller/troubleshooting/troubleshoot-ingress-controller/

delete cluster, start again
```shell
ctlptl delete cluster kind-kind
ctlptl create cluster kind --registry=ctlptl-registry
```

cluster dump
```shell
kubectl cluster-info dump
```

ingress inforomation
```shell
kubectl get services -n ingress-nginx
kubectl get ingress -n ingress-nginx
nginx -T
```
