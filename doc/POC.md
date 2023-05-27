# [Set up Argocd cluster](https://argo-cd.readthedocs.io/en/stable/getting_started/):
-----
## Install k3d

```shell
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

## Create cluster argocd:
```shell
k3d cluster create argocd --servers 1 --agents 3
```

## Create namespace argocd:
```shell
kubectl create namespace argocd
```
## setting namespace for default context:
```shell
kubectl config set-context --current --namespace kube-system
```

## Install argocd into namespace:
```shell
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Show information:
```shell
kubectl get nodes
```
```shell
kubectl get all -A
```

## Expose port in argocd:
```shell
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## In new terminal:
- Receive row password for entering in system:
```shell
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

## UI Acess:
- open https://localhost:8080/ In browser
- trust ssl certificate (in "advanced"), proceed
- In order to enter into argocd use login "admin" and password, which was received from the last command
-----
## Remove namespace argocd:
```shell
kubectl delete namespace argocd
```

## Remove cluster argocd:
```shell
k3d cluster delete argocd
```