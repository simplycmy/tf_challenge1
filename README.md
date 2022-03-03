<div id="top"></div>

<!-- ABOUT THE PROJECT -->
## The Challenge

[Challenge is based on this given link!](https://docs.microsoft.com/en-us/azure/developer/terraform/create-vm-scaleset-network-disks-hcl)

This is a Terraform challenge given by my course instructor, Bryan Lim. 

We are tasked to run the tutorial code and make it work by running it in our working O/S (Windows / Ubuntu / Mac). The choice is yours. 
You may face some problem along the way, but fear not, I have provided the steps by steps guide. 

I have also included the edited files in this git repo. Please use it for reference if you are stuck. Thank you. 

<p align="right">(<a href="#top">back to top</a>)</p>

## Problems faced

FYI, I am running the code with Windows 10 system. 
For people who like to run in WSL using Ubuntu distro. 

You are required to change DNS to 1.1.1.1

Simply edit the <etc/resolv.conf> file and add nameserver 1.1.1.1 (Solution provided by classmate, Brandon V & SY)

If you dont do that, there will be issue when you use command "terraform apply"

Lastly, you may also need to update your system. Simple run "sudo apt-get update" and "sudo apt-get upgrade" for Ubuntu system. (Solution by Alwin Poon)

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

To run this terraform challenge in windows, you need to first install a few dependanies in your system.

Note: You need to run Windows powershell in adminstrator mode to install the software with the commands given. 


### Prerequisites

Below is the list of commands to install them. Please install them in sequence. 
* [Chocolatey](https://chocolatey.org/install)
 
  ```sh
  Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
  ```
  
* [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)
  ```sh
  choco install terraform
  ```
  
* [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-powershell)
  ```sh
  $ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; rm .\AzureCLI.msi
  ```

<p align="right">(<a href="#top">back to top</a>)</p>

## Verification

After installation, verify that Terraform and Azure CLI by typing 2 separate command into Powershell. 

1- terraform

2- az

## Step by Step guide

1 - Create a Azure sandbox from ACG (A Cloud Guru). 
<p align="center">
  <img width="460" height="300" src="https://github.com/simplycmy/gif/blob/main/playground.PNG">
</p>

2 - Log into the Azure sandbox account using the user / password given. Copy and take note of the resource group name. 
<p align="center">
  <img width="460" height="300" src="https://github.com/simplycmy/gif/blob/main/resourcegroup.PNG">
</p>

3 - Create a terraform challenge folder and change directory into it. 
```sh
  cd <name of folder created>
  ```

4 - Proceed to create main.tf, varibles.tf, output.tf and web.conf in the challenge folder. Copy and paste the code from the [Tutorial link](https://docs.microsoft.com/en-us/azure/developer/terraform/create-vm-scaleset-network-disks-hcl)

5 - In variables.tf, change the default to the resource group name found in the Azure sandbox.
<p align="center">
  <img width="850" height="200" src="https://github.com/simplycmy/gif/blob/main/resoursegroupname.PNG">
</p>

6 - In main.tf, change the following code. 
* Add skip_provider_registration = true
<p align="center">
  <img width="600" height="200" src="https://github.com/simplycmy/gif/blob/main/change1.PNG">
</p>

* Comment the list of code to prevent creating new resource group.
 <p align="center">
  <img width="600" height="200" src="https://github.com/simplycmy/gif/blob/main/change2.PNG">
</p>

* Replace all resource_group_name to var.resource_group_name
 <p align="center">
  <img width="600" height="200" src="https://github.com/simplycmy/gif/blob/main/change3.PNG">
</p>

* Add delete_data_disks_on_termination = true. This is to delete the OS disk automatically when VM is deleted. Found by SY.
 <p align="center">
  <img width="600" height="200" src="https://github.com/simplycmy/gif/blob/main/changes4.PNG">
</p>

7 - Save all the changes made to the files. Ensure you are still inside the challenge folder and run the following command in sequence. 
* ```sh
  az login -u <username provided from sandbox> -p <password>
  ```
* ```sh
  terraform init
  ```
* ```sh
  terraform plan -out main.tfplan
  ```
* ```sh
  terraform apply "main.tfplan"
  ```
  
8 - Once resources have been successfully created, you can verify by..
* Azure portal with Resource visulizer
<p align="center">
  <img width="600" height="350" src="https://github.com/simplycmy/gif/blob/main/resourcevisual.PNG">
</p>

* Entering the load balancer address into web browser
<p align="center">
  <img width="600" height="350" src="https://github.com/simplycmy/gif/blob/main/address.PNG">
</p>

9 - Once you are happy and all works well. You may proceed to delete the resource with terraform destory.
```sh
  terraform destroy
  ```


<p align="right">(<a href="#top">back to top</a>)</p>
