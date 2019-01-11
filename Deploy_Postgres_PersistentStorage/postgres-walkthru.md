

#  Postgres in Kubernetes on persistent storage

  This tutorial was created to solidify the Kubernetes concepts of ConfigMaps, Persistent Volume Claims, Deployments, and Services.

# Step 1: Create Postgres config maps resource
`kubectl create -f ./postgres-configmap.yaml`

# Step 2: Create storage related deployments
`kubectl create -f ./postgres-storage.yaml`

# Step 3: Create Postgres deployment
`kubectl create -f ./postgres-deployment.yaml`

# Step 4: Create Postgres Service 
`kubectl create -f ./postgres-service.yaml`

If you change over to the diretory where the yaml files are 
located you can just cut-and-paste the lines below.

`cd </yaml file dir>`

`kubectl create -f ./postgres-configmap.yaml`

`kubectl create -f ./postgres-storage.yaml`

`kubectl create -f ./postgres-deployment.yaml`

`kubectl create -f ./postgres-service.yaml`

# Step 5: Connect to PostgreSQL
For connecting PostgreSQL, we need to get the Node port from the service deployment.
`kubectl get services postgres`

In my case, the previous command showed my port was 32447.
On Windows, this will do the trick. 

`sql -h localhost -U postgres --password -p 32447 postgresdb`

On Ubuntu, you'll need to replace localhost with the Minikube IP. To get this IP, type:
`minikube ip`
`sql -h <MinikubeIP> -U postgres --password -p 32447 postgresdb`


#Troubleshoot

Check listening ports (Windows)
`netstat -a -b` 

Check listening ports (Ubuntu)
`netstat -plnt` 

