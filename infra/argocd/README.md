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
