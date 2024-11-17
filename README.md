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
![image alt](https://github.com/sheriharish/static-website/blob/557be6a67d4ab492c2cd05acc48f5c72fd7ff93e/mdimages/1.png)<br><br>
2.	Create the Azure container registry using the ARM template:<br>
 ARM template is a JSON file that defines the infrastructure and configuration for your Azure resources. It's a declarative way to specify what resources you want to deploy, rather than writing a series of commands to deploy them. <br>
Here we used the ARM template to create the resource ACR (azure container registry).<br>
![image alt](https://github.com/sheriharish/static-website/blob/34a32462e936d0ecb9712eb3fde2a728027306a0/mdimages/2.png)
Deploy this ARM template in the resource group of RG1 by using the below command from .Json file path.<br>
[az deployment group create - -resource-group RG1 - -template-file azure-container-registry.json] <br>
![image alt](https://github.com/sheriharish/static-website/blob/34a32462e936d0ecb9712eb3fde2a728027306a0/mdimages/3.png)<br><br>
Graphical user interface or portal view:<br>
![image alt](https://github.com/sheriharish/static-website/blob/34a32462e936d0ecb9712eb3fde2a728027306a0/mdimages/4.png)<br><br>
3.	Create the Ubuntu VM using azure cli command:<br>
[az vm create –n <vm-name> -g <resource-group> --image <image-name> --admin-username <username> --admin-password <password> --sku <>].<br>
![image alt](https://github.com/sheriharish/static-website/blob/34a32462e936d0ecb9712eb3fde2a728027306a0/mdimages/5.png)<br><br>
portal view:<br>
![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/6.png)<br><br>
4.	Login into the Ubuntu VM and install Azure cli, Docker cli and Git in it. <br>
![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/7.png)<br><br>
Installing of Azure CLI:(curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash).<br>
![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/8.png)<br><br>
Installing Docker CLI: (curl -fsSL https://get.docker.com -o get-docker.sh).<br>
![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/9.png)<br><br>
Installing Git: (sudo apt install Git)<br>
![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/10.png)<br><br>
5.	Now clone the static website from GitHub repository:<br>
       Use the command [git clone <GitHub http link >].<br>
 ![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/11.png)<br><br>
 6.	Create the Docker file to configure the static website with nginx web server.<br>
 ![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/13.0.png)<br><br>
 docker file:<br>
 ![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/12.png)<br><br>
 7.	Now build the image from the dockerfile:<br>
 ![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/13.png)<br><br>
 8.	Login to the azure container registry, then tag the image and push into it.<br>
 ![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/15.png)<br><br>
 Image is uploaded in the azure container registry as show below figure.<br>
 ![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/16.png)<br><br>
 9.	Creating of azure container instance (ACI) using Azure CLI.<br>
 ![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/17.png)<br><br>
 Portal view:<br>
 ![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/18.png)<br><br>
 10.	Now copy the FQDN (fully qualified domain name) or IP address of ACI and brows it in any browser. Then our static website gets alive.<br>
![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/19.png)<br>
![image alt](https://github.com/sheriharish/static-website/blob/1d870b4c4301b0ec46abb465e6870c5d2e9bd76e/mdimages/20.png)<br><br>
## Conclusion: 
By leveraging Azure Container Instances (ACI), you can efficiently and cost-effectively deploy static websites to the cloud. ACI's server less nature and rapid deployment capabilities make it an ideal solution for hosting static content.

 
 






