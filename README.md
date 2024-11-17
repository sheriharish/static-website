# Deploying of static website using azure container instance (ACI)

## Project overview:
Deploying a Static Website Using Azure Container Instances (ACI)
## Project Goal:
To efficiently and cost-effectively deploy a static website to Azure using Azure Container Instances (ACI), leveraging its server less nature and rapid deployment capabilities.
## Project Scope:
•	Static Website: A collection of HTML and CSS files that don't require server-side processing.<br>
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
1.	Create the resource group using custom azure cli commands:<br>
[az group create - -name <resource-group-name> - -location <location-name>]<br>
Ex: az group create - -name RG1 - -location centralindia <br>
![image alt](https://github.com/sheriharish/static-website/blob/557be6a67d4ab492c2cd05acc48f5c72fd7ff93e/mdimages/1.png)
2.	Create the Azure container registry using the ARM template:<br>
 ARM template is a JSON file that defines the infrastructure and configuration for your Azure resources. It's a declarative way to specify what resources you want to deploy, rather than writing a series of commands to deploy them. <br>
Here we used the ARM template to create the resource ACR (azure container registry).<br>
![image alt](https://github.com/sheriharish/static-website/blob/34a32462e936d0ecb9712eb3fde2a728027306a0/mdimages/2.png)<br><br>
Deploy this ARM template in the resource group of RG1 by using the below command from .Json file path.<br>
[az deployment group create - -resource-group RG1 - -template-file azure-container-registry.json] <br>
![image alt](https://github.com/sheriharish/static-website/blob/34a32462e936d0ecb9712eb3fde2a728027306a0/mdimages/3.png)
Graphical user interface or portal view:<br>
![image alt](https://github.com/sheriharish/static-website/blob/34a32462e936d0ecb9712eb3fde2a728027306a0/mdimages/4.png)
3.	Create the Ubuntu VM using azure cli command:<br>
[az vm create –n <vm-name> -g <resource-group> --image <image-name> --admin-username <username> --admin-password <password> --sku <>].<br>
![image alt](https://github.com/sheriharish/static-website/blob/34a32462e936d0ecb9712eb3fde2a728027306a0/mdimages/5.png)





