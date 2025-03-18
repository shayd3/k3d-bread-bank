# k3d-bread-bank
kubernetes related configs using k3d - playground purposes

## Deploying the cluster

```bash
k3d cluster create --config ./assets/cluster.yml
```

## Mac Bonjour

Mac OS has a feature called Bonjour which allows you to resolve hostnames to IP addresses. In this case, we are using `bread-bank.local` to resolve to the IP address of the cluster.

There is a test nginx that is used for testing

```bash
kubectl apply -f manifests/nginx-deployment.yaml
```


you can hit the nginx service by running (locally or on other devices in the same network)
```bash
curl http://bread-bank.local:8080
```
