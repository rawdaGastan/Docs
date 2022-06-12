# Kubernetes

kubectl port-forward svelte-7944f6f5b9-xcfnp  8080:8080

## minikube
minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

- to start a new cluster
```
minikube start --driver=docker
```

- error : Exiting due to MK_USAGE: Docker has only 15867MB memory but you specified 16384MB
```
minikube start --memory=8192mb
```

- commands
```
minikube status
minikube pause
minikube unpause
minikube stop
minikube delete --all --> deletes all clusters
```
```
minikube service --url <service-name>                        
```

## helm

- installation
```
sudo snap install helm --classic
```

- create helm charts
```
helm create <name>
ls <name>

helm lint <path of chart>  ----> errors
helm template <path of chart> --debug ----> errors
helm install <name> <path> --dry-run

```



```
kubectl expose pod nginx --port=80 --name nginx-service --type=NodePort --dry-run=client -o yaml
```
