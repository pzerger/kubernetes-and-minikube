
# Publishing workloads on Kubernetes using Minikube

Your first workload is a "Hello World" type workload. This is a great way to quickly validate your Minikube deployment is functional. 

`kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.10 --port=8080`

Output will be 'deployment "hello-minikube" created'


> **NOTE:** kubectl run --generator=deployment/apps.v1 is DEPRECATED and will be removed in a future version. 
> Use `kubectl run --generator=run-pod/v1` or `kubectl create` instead.


### Make the service accessible 

`kubectl expose deployment hello-minikube --type=NodePort`

service "hello-minikube" exposed

We have now launched an echoserver pod but we have to wait until the pod is up before curling/accessing it via the exposed service.

To check whether the pod is up and running we can use the following:

`kubectl get pod`

NAME                              READY     STATUS              RESTARTS   AGE
hello-minikube-3383150820-vctvh   0/1       ContainerCreating   0          3s

We can see that the pod is still being created from the ContainerCreating status

`kubectl get pod`

NAME                              READY     STATUS    RESTARTS   AGE
hello-minikube-3383150820-vctvh   1/1       Running   0          13s

We can see that the pod is now Running and we will now be able to curl it:

`curl $(minikube service hello-minikube --url)`

### Scale it up

`kubectl scale --replicas=3 deployment/hello-minikube`

### Scale it down
`kubectl scale --replicas=1 deployment/hello-minikube`

### Watch pod terminating 

`kubectl get pods`

### Delete the service 

`kubectl delete services hello-minikube`

service "hello-minikube" deleted

### Delete the deployment
`kubectl delete deployment hello-minikube`

deployment "hello-minikube" deleted

### Stop minikube 

`minikube stop`

Stopping local Kubernetes cluster...
Stopping "minikube"…
