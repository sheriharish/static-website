# Deploying of static website using Azure container instance (ACI) 
## Project Overview: 
Deploying a Static Website Using Azure Container Instances (ACI) and build the image using Docker.
## Project Scope:
•	Static Website: A collection of HTML and CSS files that don't require server-side processing.
•	Azure Container Instance (ACI): A server less container service that allows you to run containers without managing virtual machines.
## Technologies and Azure Services Used:
1.	Azure CLI: Used to create the resource group, Ubuntu VM, ACR (azure container registry) and ACI (azure container instance).
2.	Ubuntu VM: Used to install Docker CLI to build and push image in easy way.
3.	ARM Template: Automated the creation of Azure container registry.
4.	ACR: we deploy our static website image into the azure container registry.
5.	ACI: A server less container service that allows you to run containers
6.	Docker: Used to build image and push it into the ACR.
7.	Dokerfile: it is used to define the environment for your static website (nginx).
8.	Vim editor: A powerful, highly customizable text editor used to configure Dockerfile.
9.	GIT: Cloned the website from GitHub onto the Ubuntu VMs using a custom script.
 ## Project Approach:
1.	Create the resource group using custom azure cli commands:
[az group create - -name <resource-group-name> - -location <location-name>]
Ex: az group create - -name RG1 - -location centralindia


