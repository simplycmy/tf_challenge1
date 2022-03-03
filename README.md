<!-- ABOUT THE PROJECT -->
## The Challenge

[Challenge is based on the given link!](https://docs.microsoft.com/en-us/azure/developer/terraform/create-vm-scaleset-network-disks-hcl)

This is a Terraform challenge given by my course instructor, Bryan Lim. 

We are tasked to make the tutorial work by running it in our working O/S (Windows / Ubuntu / Mac). The choice is yours. 
You may face some problem along the way, but fear not, I have provided the steps by steps guide. 

FYI, I am running the code with Windows 10 system. 
For people who choose to run in WSL using Ubuntu distro. You are required to change DNS to 1.1.1.1
Simply edit the <etc/resolv.conf> file and add nameserver 1.1.1.1

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

To run this terraform challenge in windows, you need to first install a few dependanies in your system.

Note: You need to run Windows powershell in adminstrator mode to run these command and install the software. 

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
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
  
* ACG (A Cloud Guru) - Azure sandbox
  ```sh
  $ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; rm .\AzureCLI.msi
  ```
  
## Verification

Verified that Terraform and Azure CLI by typing 2 separate command into Powershell. 

1- terraform

2- az

