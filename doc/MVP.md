# Setup go-demo-app :
-----

## Demo

 ![sync-demo-app](./sources/sync-demo-app.gif)

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
```shell
kubectl get pods -A
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

## Auto sync go-demo-app

### In agro CD UI:

1) create app "demo-app" (in "NEW APP")
2) "default" project
3) path "helm"
4) set source https://github.com/den-vasyliev/go-demo-app
5) Cluster URL "https://kubernetes.default.svc"
6) namespace "demo-app"
7) in "SYNC OPTIONS" -> "AUTO-CREATE NAMESPACE"
8) SYNC POLICY -> "Automatic"
9) Press "Create"

### In new Terminal run port forwarding to API Gateway:
-
 ```shell
 kubectl port-forward -n demo-app svc/ambassador 8088:80
 ```
### send file:
```shell
curl -o kubericon.png https://kubernetes.io/images/kubernetes-horizontal-color.png
```
```shell
curl -F 'image=@kubericon.png' localhost:8088/img/
```

-----
## Remove namespace argocd:
```shell
kubectl delete namespace argocd
```

## Remove namespace argocd:
```shell
kubectl delete namespace demo-app
```

## Remove cluster argocd:
```shell
k3d cluster delete argocd
```