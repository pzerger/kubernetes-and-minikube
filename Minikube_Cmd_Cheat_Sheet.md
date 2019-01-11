

# Minikube Command Cheat Sheet 
To help you get comfortable managing your Kurbernetes dev environment in minikube quickly, this document contains a wide variety of sample commands, including complex samples, for **minikube** and **kubectl**.

- [Minikube Command Cheat Sheet](#minikube-command-cheat-sheet)
- [Minikube Commands](#minikube-commands)
- [Dashboards](#dashboards)
- [Kubectl Commands](#kubectl-commands)
- [Deleting Artifacts](#deleting-artifacts)
- [Horizontal Pod Autoscaler](#horizontal-pod-autoscaler)
- [Persistent Volumes](#persistent-volumes)

# Minikube Commands 
Start Minikube Service	

`minikube start` 

Start Minikube Service with 4 cpus and 8192 of memory

`minikube start --cpus 4 --memory 8192` 

Stop Mikikube Service

`minikube stop` 

Clean the configurations and start clean (maybe also you need rm -rf ./minikube)

`minikube delete` 

List of Kubernetes versions Minikube currently supports

`minikube get-k8s-versions` 

Start with a specific version of k8s

`minikube start --kubernetes-version v1.7.5` 

View ip of Cluster

`minikube ip` 

Get the URL of service

`minikube service --url <service name>`

View the status of minikube, cluster and kubectl (Something ips change)

`minikube status`

Fix ips change, kubectl misconfigured

`minikube update-context` 

Visit the service in a browser 

`minikube service -n development hpa-example`

[back to top](#minikube-command-cheat-sheet)
# Dashboards 
You can actually type the commends below in the terminal to auto-launch the Kubernetes and/or Grafana dashboards in a browser. 

Open the Kubernetes Dashboard

`minikube dashboard` 

Open the Grafana Dashboard 

`minikube addons open heapster`

Get the Dashboard URL

`minikube dashboard --url` 

[back to top](#minikube-command-cheat-sheet)
# Kubectl Commands 
These commands will return the appropriate artifacts for the __default__ namespace. 

Nodes, Podes, Deployments, or Services, for example:

`kubectl get nodes`
 
`kubectl get pods` 

`kubectl get deployments`
 
`kubectl get services` 

`kubectl get deployments postgres`

You can add `--all-namespaces` to any of the above commands in this section to see content from all namespaces, for example: 

`kubectl get pods --all-namespaces`

`kubectl get namespaces`
 
 [back to top](#minikube-command-cheat-sheet)
# Deleting Artifacts 

Delete pods, services named 'hello-minikube'

`kubectl delete pods,services hello-minikube`

Delete service named hpa-example in development namespace

`kubectl delete service hpa-example -n development`

Delete deployment named hpa-example in development namespace

`kubectl delete deployment hpa-example -n development`

Delete all pods in namespace 'foo'

`kubectl delete --all pods --namespace=foo`

delete all namespaces

`kubectl delete --all namespaces`

Delete everything with an app label of 'postgres' 

`kubectl delete daemonset,replicaset,service,deployment,pods,rc,pvc,pv,configmap --selector=app=postgres`

Delete EVERYTHING

`kubectl delete daemonsets,replicasets,services,deployments,pods,rc,pvc,pv,configmap --all`

[back to top](#minikube-command-cheat-sheet)
# Horizontal Pod Autoscaler 
Autoscale (HPA)

`kubectl autoscale deployment hpa-example -n development --cpu-percent=50 --min=1 --max=10`

Delete all HPAs in the development namespace

`kubectl delete hpa --all -n development`

Delete HPA named hpa-example in development namespace

`kubectl delete hpa -n development hpa-example`

[back to top](#minikube-command-cheat-sheet)
# Persistent Volumes 
Persistent volumes are an important part of production life, but because minikube boots to tmpfs, it wipes most things across reboots, unless stored [in one of a few designated directories.](https://github.com/kubernetes/minikube/blob/master/docs/persistent_volumes.md) 

List persistent volumes 

`kubectl get pv `

List persistent volume claims

`kubectl get pvc `

Delete persistent volume named postgres

`kubectl delete pv postgres`

[back to top](#minikube-command-cheat-sheet)
