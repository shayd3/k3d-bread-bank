# k3d-bread-bank
kubernetes related configs using k3d - playground purposes

## Deploying the cluster

```bash
k3d cluster create --config ./assets/cluster.yml
```

## Mac Bonjour

Mac OS has a feature called Bonjour which allows you to resolve hostnames to IP addresses. In this case, we are using `bread-bank.local` to resolve to the IP address of the cluster.

Thanks mDNS! 😎

## Test Nginx Deployment
There is a test nginx that is used for testing

```bash
kubectl apply -f manifests/nginx-deployment.yaml
```

you can hit the nginx service by running (locally or on other devices in the same network)
```bash
curl http://bread-bank.local:8080
```

## Traffic flow

Find Mac IP address by running:
```bash
ifconfig | grep "inet " | grep -v 127.0.0.1
```

hit nginx service by running:
```bash
curl http://bread-bank.local:8080
```

In the case of the nginx example that is here:
* Request comes to your Mac's IP on port 8080
* k3d loadbalancer receives it
* Traefik ingress controller routes to the nginx-demo service
* Service directs to one of nginx pods
