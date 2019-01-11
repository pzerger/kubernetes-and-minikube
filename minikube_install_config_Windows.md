
# Install & configure Minikube on Windows 10 

  Step-by-step instructions to install & configure minikube on Windows 10 
  https://kubernetes.io/docs/tasks/tools/install-minikube/

# Step 1: Install Kubectl 
*If you are on Windows and using Chocolatey package manager, you can install kubectl with Chocolatey.*
If you haven't installed Chocolately yet, find instructions [HERE](https://chocolatey.org/install)

1. Run the installation command from a command prompt:

	`choco install kubernetes-cli`

2. Test to ensure the version you installed is sufficiently up-to-date:

	`code kubectl version` 

3. Change to your %HOME% directory. For example: 

	`cd C:\users\your username\`

4. Create the .kube directory:

	`mkdir .kube`

5. Change to the .kube directory you just created:

	`cd .kube`

>**NOTE:** Edit the config file with a text editor of your choice, such as Notepad.

# Step 2: Hyper-V Virtual Switch 

Find the name of your external virtual switch or create one. In this case, we generally create one called 'minikube' for ease of reference.

# Step 3: Install Minikube 

For Windows, download the **minikube-installer.exe** from the list at  https://github.com/kubernetes/minikube/releases

Default install directory is C:\Program Files (x86)\Kubernetes\Minikube


# Step 4: Update PATH & Configure Minikube Environment Variable

The default install directory is 'C:\Program Files (x86)\Kubernetes\Minikube'. 

1. Add this directory to the PATH system variable. 

2. Also, configure this path as as the value for an environment variable named MINIKUBE_HOME.

# Step 5: Launch Minikube 
It's a good idea to launch Minikube with verbose logging enabled, so if it fails to start, you will have some detail as to how. After you 
install Minikube, the statement below will download the Minikube .iso, setup the VM, and establish the profile directory at "c:\users\your 
username\.minikube" NOTE: If this command hangs on starting, just close the PowerShell window, open a new one and move to the next step.

`minikube start --vm-driver hyperv --hyperv-virtual-switch "minikube"  --v=7 --alsologtostderr`

# Step 6: Make sure addons are enabled 
Sometimes the Heapster addon (which includes Grafana) is not enabled by default, and you will need this.

First, list the available addons.
`minikube addons list`

If heapster(includes grafana & influx) and metrics-server show as disabled, enable them as follows:
More on metrics-server and metrics API at https://github.com/kubernetes-incubator/metrics-server/

`minikube addons enable heapster`

`minikube addons enable metrics-server`

View the pods you just created.

# Step 7: Verify the dashboards are available 
Open the kubernetes dashboard, simply type the command below and it will open in your default browser.

`Minikube dashboard`

Open the grafana dashboard, simply type the command below and it will open in your default browser.

`Minikube addons open heapster `

# Step 8: Test with hello-minikube
If all the above are successful, proceed to [**hello-minikube workload**](./minikube_run_helloworld_workload.md) and attempt to run your first workload.

# Additional Guidance

Because minikube sometimes hangs on the 'minikube stop' command in this build, you may just want to leave minikube running. It takes < 1GB ram if you delete your running services. 