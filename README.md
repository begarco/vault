# vault

helm repo add hashicorp https://helm.releases.hashicorp.com
helm search repo hashicorp/vault

helm install vault hashicorp/vault --namespace vault --version 0.22.1 --set "server.ha.enabled=true" --set "server.ha.replicas=5" --dry-run

helm install vault hashicorp/vault --namespace vault --version 0.22.1 -f ./vault-configuration-values.yaml --dry-run

kubectl --namespace='vault' create secret tls tls-secret --cert=path/to/tls.cert --key=path/to/tls.key

```
apiVersion: fleet.cattle.io/v1alpha1
kind: GitRepo
metadata:
  name: vault
  # This namespace is special and auto-wired to deploy to the local cluster
  namespace: fleet-local
spec:
  # Everything from this repo will be ran in this cluster. You trust me right?
  repo: "https://github.com/begarco/vault"
  paths:
  - simple
```