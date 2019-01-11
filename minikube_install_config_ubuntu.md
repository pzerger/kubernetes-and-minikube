
# Install & configure Minikube on Ubuntu  

Step-by-step instructions to install & configure minikube on Ubuntu 18.04 LTS 
Official docs @ https://kubernetes.io/docs/tasks/tools/install-minikube/


# Step 1: Install Virtualbox 
Use the commands below, or find step-by-step instructions at https://linuxize.com/post/how-to-install-virtualbox-on-ubuntu-18-04/

`sudo apt update`
`sudo apt install virtualbox virtualbox-ext-pack`

# Step 2: Install Kubectl (using native package mgmt)
# https://kubernetes.io/docs/tasks/tools/install-minikube/#install-kubectl

`snap install kubectl --class` 

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