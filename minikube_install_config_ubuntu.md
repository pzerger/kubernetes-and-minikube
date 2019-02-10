
# Install & configure Minikube on Ubuntu  

Step-by-step instructions to install & configure minikube on Ubuntu 18.04 LTS 
Official docs @ https://kubernetes.io/docs/tasks/tools/install-minikub

# Step 1: Install Virtualbox 
Use the commands below, or find step-by-step instructions at https://linuxize.com/post/how-to-install-virtualbox-on-ubuntu-18-04/

`sudo apt update`
`sudo apt install virtualbox virtualbox-ext-pack`

# Step 2: Install Kubectl (using native package mgmt)
https://kubernetes.io/docs/tasks/tools/install-minikube/#install-kubectl

`snap install kubectl --classic` 

# Step 3: Install minikube (using native package mgmt)
https://kubernetes.io/docs/setup/minikube/#installation

This will take a few minutes, but is largely hands-free.

`curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.32.0/minikube-linux-amd64 && chmod +x minikube && sudo cp minikube /usr/local/bin/ && rm minikube`


# Step 4: Launch Minikube 
https://kubernetes.io/docs/setup/minikube/
It's a good idea to launch Minikube with verbose logging enabled, so if it fails to start, 
you will have some detail as to how. After you install Minikube, the statement below will 
download the Minikube .iso, setup the VM, and establish the profile directory at "c:\users\your username\.minikube"

`minikube start --vm-driver virtualbox  --v=7 --alsologtostderr`

# Step 5: Make sure addons are enabled 
Sometimes the Heapster addon (which includes Grafana) is not enabled by default, and you will need this.

First, list the available addons.
`minikube addons list`

If heapster(includes grafana & influx) and metrics-server show as disabled, enable them as follows:
More on metrics-server and metrics API at https://github.com/kubernetes-incubator/metrics-server/

`minikube addons enable heapster`

`minikube addons enable metrics-server`

View the pods you just created.

# Step 6: Verify the dashboards are available 
Open the kubernetes dashboard, simply type the command below and it will open in your default browser.

`Minikube dashboard`

Open the grafana dashboard, simply type the command below and it will open in your default browser.

`Minikube addons open heapster `

# Step 7: Test with hello-minikube
If all the above are successful, proceed to [**hello-minikube workload**](./minikube_run_helloworld_workload.md) and attempt to run your first workload.
