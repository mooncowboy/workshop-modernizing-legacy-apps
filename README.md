# Modernizing Legacy Apps workshop
Content for the Modernizing Legacy Apps workshop delivered for Microsoft partners in Lisbon. Jan 8, 2019.

# Goals

- Understand where your apps are in the journey to cloud
- Understand the parts of your apps that are preventing you to ship them faster and what you can implement now to fix it
- Get to know the Azure platform for modernizing applications
- Become familiar with the tooling with some hands-on Docker, orchestrators and serverless technologies
- Use DevOps as a base for better software development

# Main Topics
- Containers
- Microservices
- Serverless
- DevOps

# Not Covered

- Advanced docker and kubernetes topics (eg: networking, persistency, ingress controllers, ...)
- Deep dive into specific services (AKS, Service Fabric, etc...)
- Microservices patterns
- Hands-on complex applications

# Schedule

TBD

# Pre-requisites

## Azure Subscription

You need access to a subscription where you can create resources including service principals. You can use your own or a voucher (if given to you).

To activate the voucher:

1. Do **NOT** use your work account or an account that has previously activated a voucher
2. In an **In-Private / Incognito** browser window, go to <https://www.microsoftazurepass.com/>  
3. Sign in (or [create a Microsoft Account](https://account.microsoft.com/account?lang=en-us) if you need to)
4. Follow the steps to activate the voucher

## Azure DevOps Organization 

Using the same account as above, login to [Azure DevOps Services](https://azure.microsoft.com/en-us/services/devops/) (or [create an account](https://azure.microsoft.com/en-us/services/devops/))

**In the Azure Portal** (not in Azure DevOps), create a new DevOps Project choosing the following:

- .NET
- ASP.NET Core
- Kubernetes Service

**NOTE:** You don't need to wait for this to finish right now, so you may proceeed.

It will create a new Azure DevOps project with repo, build and release pipelines. It will also create an Azure Container Registry and Kubernetes Service. 

## Tooling

* Docker (to run Linux containers)
* Azure CLI or Azure Cloud Shell
* kubectl 
* Visual Studio Code with Docker and Kubernetes extensions (recommended)

If you don't have the tools above in your local computer, you can launch an available on GitHub by following the steps below.

## Using the Ubuntu VM with Docker

https://github.com/Azure/azure-quickstart-templates/tree/master/docker-simple-on-ubuntu

1. Click the **Deploy To Azure** Button
2. Specify parameters:
    - Resource Group: create a new one
    - Location: North or West Europe
    - Admin Username and Password: (choose your own)
    - Dns Name: must be globally unique (eg: rifiel-ubuntudockervm)
3. Once started, connect to the VM via SSH
4. Install git `sudo apt-get install git`
5. Make sure docker is running by typing `docker run hello-world`

# Lab Steps

## Containers

Available in [01-containers.md](01-containers.md)

## Microservices

Available in [02-microservices.md](02-microservices.md)

## Serverless

TBD

# Microsoft Cloud Workshop student guides

To be completed after labs.

[Microservices](https://github.com/Microsoft/MCW-Microservices-architecture/blob/master/Whiteboard%20design%20session/WDS%20student%20guide%20-%20Microservices%20architecture.md) 

[Serverless](https://github.com/Microsoft/MCW-Serverless-architecture/blob/master/Whiteboard%20design%20session/WDS%20student%20guide%20-%20Serverless%20architecture.md)
