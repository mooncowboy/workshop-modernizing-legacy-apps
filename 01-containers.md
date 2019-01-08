# Containers Lab

In this lab, you'll get familiar with:
- Running an existing Docker image
- Building Docker images
- Creating a Dockerfile
- Pushing to a registry
- Using Azure DevOps to automate the build and release 
- Understanding how to optimize a  Dockerfile

## Run an existing docker image

In Azure CLI or Cloud Shell, create an Azure Container Instance

`az container create -n myngxin -g <your_rg_here> --ip-address public --image library/nginx`

Notice the IP Address once the operation completes and browse to that address. You've just launched a container.

## Build a docker image

**Pre-requisites:** Make sure you've gone thru the steps in [README.md](README.md) before proceeding

As a 1st step, let's build an ASP.NET Core Docker image. Notice that we don't have ASP.NET installed on the VM.

1. Go to the src/01-containers folder
2. Type `docker build -t mvc1 .`
3. Type `docker run --rm -p 80:80 mvc1`
4. In the Azure Portal, find the IP address of the VM and browse to it. You should see your application running

## Pushing to a registry

In the Azure Portal, go to the Azure Container Registry that was created by the DevOps Project, then Settings -> Admin User. Make sure it's enabled and take note of the username and password (one of them).

Your login server below should be replaced with <something>.azurecr.io.

1. Authenticate with Docker by typing `docker login <login_server> -u <username> -p <password>`
2. Tag the image so it includes the container registry: `docker tag mvc1 <login_server>/mvc1`
3. Push it `docker push <login_server>/mvc1`

## Run your image

Repeat the ACI command, but this time use your custom image

`az container create -n myimage -g <your_rg_here> --ip-address public --image <login_server>/mvc1`

## Using Web App

Container Instances are just one way of running containers. Another way is using Web Apps. 

1. In the Azure Portal, create a new Web App
2. Specify OS = Linux
3. Specify Publish = Docker Image
4. Choose Azure Container Registry and select your uploaded docker image

## Automate with Azure DevOps

Start by forking this repo in GitHub or clone it to Azure DevOps.

Create a build pipeline that:

1. Builds the Docker image using the `Dockerfile.optimized` file
2. Pushes the result to Azure Container Registry
3. Make sure the build is triggered automatically (enable continuous integration)
4. Change the [src/01-containers/Views/Home/Index.cshtml](src/01-containers/Views/Home/Index.cshtml) file by adding a div with your name
5. Git add, commit and push to the master branch
6. Check if the build was triggered and the image was pushed to ACR

## Optimize Dockerfile

Compare the `Dockerfile` and `Dockerfile.optimized` files. Can you understand the differences? 