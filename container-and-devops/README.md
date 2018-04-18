# Introduction

In the Container and DevOps workshop, attendees will deploy Azure Container Service through scale, load balancing, and service discovery. 
In addition, 
* Create & run a Docker Application
* Deploy to the Azure Container Service
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
* Note that you have access to one resource group  
* Navigate to the resource group and view the already existing resources such as Container Service, build agent Linux VM, etc.
* Verify that following resources are predeployed:
  1. Build Agent Linux VM
  2. Azure Container Registry
  3. Azure Container Service
* Build Agent Linux VM has been configured with the following:
  1. Packages are updated and Docker engine is installed
  2. Azure CLI 2.0
  3. Kubernetes CLI
  4. FabMedical files are downloaded into the User's home directory

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

Build Agent Linux VM (Ubuntu Server 16.04 from Canonical) is pre-provisioned with additional tools configured as well as RDP enabled.
Users can verify that the VM is installed with Azure CLI 2.0, Kubernetes CLI by executing the following commands:
* az --version
* kubectl 

Also verify that the user is able to RDP into the virtual machine as well as FabMedical directory is there in the users home directory
FQDN of the virtual machine and administrator credentials are provided in the lab details page.

# Connect to Build Agent Linux VM

* **Users can connect to the Linux VM using SSH Client or RDP client and execute the commands from either SSH Client or Terminal inside Linux VM**
* For SSH, If you are using a Windows machine, you would need a SSH client for connecting to a Linux Virtual Machine. Putty is the most widely used SSH client for windows. If you are using Mac or Linux based machines, you can use the bash terminal.
* If the user is accessing the Linux VM via putty, he will need to enable tunnelling to the local machine.

**Using SSH Client from your local machine:** 

If the user is using Windows local machine and putty to login to the Linux VM, go to step 1.  
Else If the user is using a Linux terminal or Mac bash terminal or Git Client for Windows, go to step 13 

 **Using RDP Client from your local machine:**
 
Start with step 15

1.	Now Download a SSH Client from here, if you don’t already have one. http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html

2.	Now run putty.exe from the users PC.

3.	An application window pops up when user run putty.exe.

4.	Enter the linuxVMDnsName of the VM to the Host Name (or IP address) box of the putty. Port will be 22 by default.

5.	Go to the Tunnels section in PuTTY, 
 
6.	Now, user will configure a specific Local port 8001, that will redirect to 8001 of the build agent Linux VM. 

7.	Provide the following details and click on Add:
   Source Port: 8001
   Destination: 127.0.0.1:8001
Then Click on Open.
 
8.	Now a new terminal will pop and user will be connected to the build agent virtual machine.

9.	The PuTTY Security Alert will pop up. Click on Yes.

10.	Login using the adminUsername and adminPassword for the build agent Linux VM.
 
11.	After entering the username and password user can start accessing the build agent Linux VM.
 
12.	Now skip to Exercise 1 Task 1 Step 1

13.	For Mac or Linux or git client( Windows), use the following command to SSH into the build agent VM
ssh -L 8001:127.0.0.1:8001 labuser@[linuxVmDnsName]

14.	Now, skip to Exercise 1 Task 1 Step 1

15.	Login in to the Linux VM using environment credentials you received.
 
16.	Once you are in the home screen, Click on Terminal Emulator at the bottom screen
 
17.	Now terminal window will pop up and you can continue to Exercise 1 Task 1 Step 1


# Known Issues

* Some instance can have problem with RDP, such users can sign up again and get a new instance.
* Users should do the entire lab either by RDP and executing from the terminal inside the linux VM or by
connecting to the linux agent using SSH Client.
* If the user is connecting to the linux using an SSH Client, he should have configured tunneling to the local machine, else the user won't be able to accept the Kubernetes Management portal on Local Machine

# Notes to Instructors / Proctors

* All the tasks in Before Hands on Lab section is pre deployed and given to the user except Windows 10 Development VM
* Windows Jump VM is not needed anymore to complete this workshop
* RDP is enabled on build agent linux VM. Users can access this VM and complete the workshop
* **Users can connect to the Linux VM using SSH Client or RDP client and execute the commands from either SSH Client or Terminal inside Linux VM** as mentioned in  [Connect to Build Agent Linux VM](https://github.com/PraveenAnil/Microsoft-Cloud-Workshop/tree/master/container-and-devops#verify-azure-access) section


The FabMedical Starter files are already downloaded in the VM at users home directory.
To avoid any issues while trying to copy from the document, kubernetes-web.yaml file is already added into the users home directory.


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.



