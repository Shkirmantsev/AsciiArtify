# Concept

## Using of different implementations of kubernetes

Check whether the kubectl and kubeadm are installed
- [install kubectl on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
- [Install and Set Up kubectl on macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
- [Install and Set Up kubectl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)
- [Installing kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)

### Example of using of minikube
----

#### Install minikube (Linux):
```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
```shell
 sudo install minikube-linux-amd64 /usr/local/bin/minikube
 ```

 #### start cluster with minikube:

```shell
 minikube start
 ```

#### See pods

```shell
kubectl get pods -A
```

#### Start dashboard in other terminal window

```shell
kubectl get pods -A
```

#### Deploying and Testing a Sample App

```shell
kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0
```

#### Next, expose the web deployment as a Kubernetes Service, specifying a static port where it will be accessible with ```--type=NodePort``` and ```--port=8080```:
```shell
kubectl expose deployment web --type=NodePort --port=8080
```

#### check whether the service is running

```shell
kubectl get service web
```

#### Now you can use minikube to retrieve a URL that is accessible outside of the container. This URL will allow you to access the hello-app service that is running on port 8080 inside your cluster:

```shell
curl $(minikube service web --url)
```

#### Remove deployment:
```shell
kubectl delete deployment web
```

#### Remove cluster:
```shell
minikube delete
```
-----