# Description
This app utilises [my small FastAPI app](https://github.com/IIaKyJIuH/currency_chain_converter) in order to show, how to deal with Kubernetes. 

# Prerequisites
In order to test this project locally, you ought to install [Minikube](https://minikube.sigs.k8s.io/docs/start/) according to your OS, please, follow those steps and only then proceed.

Kubernetes is a tool to organise multiple docker container instances (nodes) in order to sustain highly loaded apps. There are two types of nodes: Master and Worker. The first one, as you might have guessed, is responsible for servicing, and the second one - for running application containers themselves.

Minikube is a superstructure over Kubernetes, which allows you to configure just 1 node that will do all that stuff, so you can test your infrastructure with ease.  

# Initialisation
Firstly, we should start our minikube instance. But before that you should determine, which driver you will use onwards.
If your OS is Windows, I strongly recommend you to use ["hyperv"](https://minikube.sigs.k8s.io/docs/drivers/hyperv/) driver, otherwise "docker" driver would be enough.
```
minikube start --driver=<chosen driver>
```
You might get an error with permissions, in order to cope with that, rerun your command line or terminal with Administrator privilegies.

Finally, after a short configuration time, you can check if it was set correctly by using this command:
```
minikube status
```

# Configuration
Type in the following command inside the root of the project
```
kubectl apply -f .
```
This will set the configuration from the .yaml files and initiate the pods (containers). 
You will have to wait for some time in order for the pods to run.

You can check the status of the pods interactively by using:
```
kubectl get pods -w
```

# Connect to the instance
Type this command in the command line or the terminal:
```
minikube service fast-api
```
This will bring you to the browser, where you will see the project.