# Cert Manager Configuration

## 1. Install cert-manager helm chart

Add cert-manager repo if needed

```sh
helm repo add jetstack https://charts.jetstack.io --force-update
```

Install cert-manager helm chart

```sh
helm install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.16.2 \
  --set crds.enabled=true
```

Change to cert-manager namespace

```sh
kubens cert-manager
```

## 2. Configure Porkbun webhook (if needed)

Clone repository and follow instructions

```sh
gh repo clone mdonoughe/porkbun-webhook
```