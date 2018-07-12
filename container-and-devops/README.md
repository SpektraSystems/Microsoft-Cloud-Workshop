# Introduction

In the Container and DevOps workshop, attendees will deploy Azure Kubernetes Service through scale, load balancing, and service discovery. 
In addition, 
* Create & run a Docker Application
* Deploy to the Azure Kubernetes Service
* Scale the application and test availability

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **30 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed. Also, for multi-day workshops, all virtual machines will be shutdown at 7 PM local time and start at 8AM local time.

# Verify the pre-provisioned Environment

* Open a browser instance in InPrivate / incognito mode and navigate to https://portal.azure.com 
* Login to the portal using Azure Credentials issued for your environment.  
* Once you are logged in to the portal, navigate to Resource Groups. 
* Note that you have access to two resource groups:
  1. **ODL-devops-containers-XXXXX-01** contains Build Agent VM
   [Note: For all tasks which involve deployment, use **ODL-devops-containers-XXXXX-01** ]
  2. **ODL-devops-containers-XXXXX-02** contains Windows Jump VM
  
* Navigate to the resource group and view the already existing resources such as Container Service, build agent Linux VM, etc.
* Verify that following resources are predeployed in the resource group **ODL-devops-containers-XXXXX-01**:
  1. Build Agent Linux VM "**fabmedicalagent**"and associated resources such as NSG, VNET, Public IP, etc
  2. Azure Container Registry
  3. Azure Kubernetes Service with the following name "**fabmedical-xxxx**"
  
  Build Agent Linux VM has been configured with the following:
  1. Packages are updated and Docker engine is installed
  2. Installed MongoDB Clients, Azure CLI 2.0, Kubernetes CLI, Bower, NodeJs 
  
* Verify that following resources are predeployed in the resource group **ODL-devops-containers-XXXXX-02**:
  1. Windows Jump VM "**LABVM**"and associated resources such as NSG, VNET, Public IP, etc
  
  Windows Jump VM has been configured with the following:
  1. Visual Studio Code 
  2. Git Bash
  3. Putty
 

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

1. **Windows JumpVM** 
  OS: Visual Studio CE 2017 on Windows Server 2016
  You can RDP into this VM using the credentials and FQDN provided in the Lab details page.
  Verify that Git Bash and Putty is there in the Desktop, and Visual Studio Code is installed.

2. **Build Agent Linux VM** (Ubuntu Server 16.04 from Canonical) is pre-provisioned with additional tools configured as well as RDP enabled.
You can verify that the VM is installed with Azure CLI 2.0, Kubernetes CLI by executing the following commands:
* az --version
* kubectl 

  Also verify that you can RDP into the virtual machine if you wants to directly RDP to the Linux VM
  FQDN of the virtual machine and administrator credentials are provided in the lab details page.
 

# Connect to Build Agent Linux VM

* **You can connect to the build agent Linux VM using:**
  1. SSH Client in the Windows Jump VM
  
     Putty and Git Bash is already installed in the Windows Jump VM
  2. RDP Client on your local machine


1. **Using SSH Client from the Windows Jump VM** 
 
   * **If you are using Git Bash**
  
    1. Use the following command to SSH into the build agent VM
    
       ssh -L 8001:127.0.0.1:8001 labuser@[linuxVmDnsName]

   * **If you are using Putty to connect** 

    1.	Login into the Windows Jump and open putty.exe from the Desktop.

    2.	An application window pops up when user run putty.exe.

    3.	Enter the linuxVMDnsName of the VM to the Host Name (or IP address) box of the putty. Port will be 22 by default.

    4.	Go to the Tunnels section in PuTTY, 
 
    5.	Now, user will configure a specific Local port 8001, that will redirect to 8001 of the build agent Linux VM. 

    6.	Provide the following details and click on Add:
       Source Port: 8001
       Destination: 127.0.0.1:8001
       Then Click on Open.
 
    7.	Now a new terminal will pop and user will be connected to the build agent virtual machine.

    8.	The PuTTY Security Alert will pop up. Click on Yes.

    9.	Login using the adminUsername and adminPassword for the build agent Linux VM.
 
    10.	After entering the username and password user can start accessing the build agent Linux VM.



 2. **Using RDP Client on your local machine:**

    1.	Using the RDP Client, Login in to the Linux VM using environment credentials you received.
 
    2.	Once you are in the home screen, Click on Terminal Emulator at the bottom screen
 
    3.	Now terminal window will pop up and you can continue to Exercise 1 Task 1 Step 1


# Known Issues

* If the Kubernetes dashboard becomes unresponsive in the browser this is an indication to return here and check your tunnel or rerun the command "**aks browse...**"
* Some instance can have problem with RDP, such users can sign up again and get a new instance or they can go to the Azure portal and restart the VM.
* Users should do the entire lab either by RDP and executing from the terminal inside the linux VM or by
connecting to the linux agent using SSH Client from the Windows Jump VM.
* If any user who is using RDP and is getting stuck at aks browse with browser not loading, they should go to the Azure portal and restart the Linux VM and then connect again and execute the az aks browse command to access kubernetes console
* If the user is connecting to the linux using an SSH Client, he should have configured tunneling to the local machine, else the user won't be able to accept the Kubernetes Management portal on Local Machine

# Notes to Attendees

* Start with [Task 13](https://github.com/Microsoft/MCW-Containers-and-DevOps/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Containers%20and%20DevOps.md#task-13-download-the-fabmedical-starter-files) from Windows Jump VM before starting with the actual exercises
* Use Git Bash for completing [Task 13](https://github.com/Microsoft/MCW-Containers-and-DevOps/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Containers%20and%20DevOps.md#task-13-download-the-fabmedical-starter-files)
* Execute the following command instead of Task 13 Step 1 in Before Hands on Lab part:

curl -L -o FabMedical.tgz https://github.com/Microsoft/MCW-Containers-and-DevOps/blob/master/Hands-on%20lab/FabMedical.tar.gz?raw=true

* Use **ODL-devops-containers-XXXXX-01** for deploying any resources to Azure
* For [Exercise 1 -> Task 7](https://github.com/Microsoft/MCW-Containers-and-DevOps/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Containers%20and%20DevOps.md#task-7-push-images-to-azure-container-registry) -> Step 13,  you can use the Service Principal details provided in the Lab Details Page


# Notes to Instructors / Proctors

* Tasks till Task 12 in Before Hands on Lab section has been pre-configured for the users
* [Task 13](https://github.com/Microsoft/MCW-Containers-and-DevOps/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Containers%20and%20DevOps.md#task-13-download-the-fabmedical-starter-files) needs to be completed by the attendee from the Windows Jump VM
* Attendees need to use Git Bash instead of WSL in Windows Jump VM to complete Before Hands on Lab Task 13
* Attendees need to execute the following command instead of Task 13 Step 1:
  
 curl -L -o FabMedical.tgz https://github.com/Microsoft/MCW-Containers-and-DevOps/blob/master/Hands-on%20lab/FabMedical.tar.gz?raw=true
 
* **Users can connect to the Linux VM using SSH Client or RDP client** and execute the commands from either SSH Client or Terminal inside Linux VM as mentioned in  [Connect to Build Agent Linux VM](https://github.com/SpektraSystems/Microsoft-Cloud-Workshop/blob/master/container-and-devops/README.md#connect-to-build-agent-linux-vm) section
* Use **ODL-devops-containers-XXXXX-01** for deploying any resources to Azure
* For [Exercise 1 -> Task 7](https://github.com/Microsoft/MCW-Containers-and-DevOps/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Containers%20and%20DevOps.md#task-7-push-images-to-azure-container-registry) -> Step 13, attendees can use the Service Principal details provided in the Lab Details Page


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
