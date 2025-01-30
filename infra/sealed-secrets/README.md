# Sealed Secrets installation and configuration

## Installation

Get latest version instructions from [Github Releases](https://github.com/bitnami-labs/sealed-secrets/releases)

## Create Sealed Secret

### Get secret in base64

```sh
echo "secret" | base64
```

### Create k8s secret manifest

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: secret-name
  namespace: namespace
data:
  auth-username: <base64 secret>
```

### Seal secret

```sh
kubeseal -f mysecret.yml -w mysealedsecret.yml
```
