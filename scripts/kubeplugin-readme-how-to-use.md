# Instruction to use kubeplugin:
---
## Instalation of plugin

1) In project root call:
```shell
cp ./scripts/kubeplugin ./scripts/kubectl-kubeplugin
```
2) In project root call:
```shell
sudo chmod +x ./kubectl-kubeplugin
```
3) In project root call:
```shell
sudo chmod +x ./scripts/kubectl-kubeplugin
```
4) In project root call:
```shell
sudo mv ./scripts/kubectl-kubeplugin /usr/local/bin
```

## Call plugin with kubectl (cluster and pod should be running)

### You can run command with all arguments (include namespace and pods) or without these two:

```shell
kubectl kubeplugin
```
or

```shell
kubectl kubeplugin pods
```

or

```shell
kubectl kubeplugin pods kube-system
```