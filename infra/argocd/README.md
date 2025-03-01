# ArgoCD

## Install

```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Create Ingress route

```sh
kubectl apply -f ingress.yml
```

## Disable internal TLS

If infinite redirect loop happens.

```sh
kubectl -n argocd edit deployments.apps argocd-server
```

Edit to this:

```
containers:
- command:
  - argocd-server
  - --insecure
  - --staticassets
  - /shared/app
```

## Login with default credentials

```
username: admin
password: <see below>
```

```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

## Install & configure ArgoCD Image Updater

### Apply installation manigests

```sh
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj-labs/argocd-image-updater/stable/manifests/install.yaml
```

### Annotate deployments

```yaml
metadata:
  annotations:
    argocd-image-updater.argoproj.io/image-list: <registry-url>/<project>/<image>
    argocd-image-updater.argoproj.io/<image>.update-strategy: latest
```

### Configure registry credentials

```sh
kubectl create secret -n argocd docker-registry harbor-secret --docker-server=<registry-url> --docker-username=<username> --docker-password=<password> --docker-email=<email>
```

### Annotate secret

```sh
kubectl -n argocd annotate secret harbor-secret argocd-image-updater.argoproj.io/registries=<registry-url>
```
