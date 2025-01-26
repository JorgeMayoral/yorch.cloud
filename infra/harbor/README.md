# Harbor Configuration

## Add Helm repo

```sh
helm repo add harbor https://helm.goharbor.io
helm repo update
```

## Create Harbor namespace

```sh
kubectl apply -f namespaces.yml
```

## Create Harbor certificate

```sh
kubectl apply -f certificate.yml
```

## Install Helm chart

```sh
helm install harbor harbor/harbor --namespace harbor --values values.yml
```

## Create K8S secret for Docker Registry

Need to be create for each namespace where is going to be used.

```sh
kubectl create secret docker-registry harbor-secret \
  --docker-server=<HARBOR_URL> \
  --docker-username=<USERNAME> \
  --docker-password=<PASSWORD> \
  --docker-email=<EMAIL>
```
