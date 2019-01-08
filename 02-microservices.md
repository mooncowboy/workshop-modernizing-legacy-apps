# Microservices Lab

In this lab, you'll get familiar with:

- Kubernetes and the kubectl command line
- Azure Kubernetes Service
- Controlling each microservice independently

## Pre-requisites 

Make sure you've gone thru the steps in [README.md](README.md) and [01-containers.md](01-containers.md) before proceeding

## Kubectl and Authentication

To interact with a Kubernetes cluster, we use the kubectl tool. Check the name and resource group of the AKS cluster created by Azure DevOps and type the following:

`az aks install-cli -n <cluster_name> -g <resource-group>`

It will install kubectl in your shell. Now we need to authenticate with the cluster:

`az aks get-credentials -n <cluster_name> -g <resource-group>`

It will create a `.kubeconfig` file in your shell that has the credentials used by kubectl.

Check that everything is working by typing `kubectl get services`

## Deploy a microservices app

To keep things fast and simple, we'll start by using one of the samples in the official kubernetes repo. 

`git clone https://github.com/kubernetes/examples`

`cd examples\guestbook`

Uncomment line 108 of guestbook-all-in-one.yaml file and so that it uses a LoadBalancer. This is the default in AKS. 

Now deploy the app with `kubectl apply -f guestbook-all-in-one.yaml`

To browse the application, we need to wait for a public IP to be assigned to the load balancer:

`kubectl get services/frontend -w`

Once the external IP is displayed, open it in a browser and check that the app is running.

## Interacting with microservices

Let's scale up and down the frontend service, while keeping the rest of the app intact. Originally, it is deployed with 3 replicas. 

`kubectl scale --replicas=2 deployment/frontend`

## Browsing your cluster

You can interact with the cluster by using commands like

`kubectl get deployments`

`kubectl get services`

You can also browse the Kubernetes UI with

`az aks browse -n <cluster_name> -g <resrouce_group>`

# Next Steps

## Smilr reference app

Have a look at the [Smilr reference app](https://smilr.benco.io/), which can be deployed to, among others, kubernetes and serverless. 

## eShopOnContainers

If you want to see a full-featured microservices app that can run in Linux and Windows, have a look at the [eShopOnContainers repo](https://github.com/dotnet-architecture/eShopOnContainers). This can be deployed to AKS or Service Fabric. 

## Further reading

- [Modernizing .NET Web & Server Apps with Windows Containers](https://dotnet.microsoft.com/learn/web/modernizing-server-apps)
- [.NET Microservices Architecture Guidance](https://dotnet.microsoft.com/learn/web/microservices-architecture)
- [Designing Distributed Systems](https://azure.microsoft.com/en-us/resources/designing-distributed-systems/)
- [Kubernetes objects on Azure](https://azure.microsoft.com/en-us/resources/kubernetes-objects-on-microsoft-azure/en-us/)