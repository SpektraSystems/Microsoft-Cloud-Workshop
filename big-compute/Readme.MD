# Introduction

The Big Compute hands-on lab will enable you to understand how to implement big compute workloads targeted at 3D rendering and media processing in Azure using Azure Batch and Azure Storage. 

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed. Also, for multi-day workshops, all virtual machines will be shutdown at 7 PM local time and start at 8AM local time.

# Verify the pre-provisioned Environment

* Users can use the **Azure Credentials** given to them to login to the Azure Portal
* One resource group **ODL_bigcompte-XXXXX-01** will be already created. In resource group **ODL_bigcompute-XXXXX-01** you will get Azure Environment with the LABVM deployed in it
* Users can select **windows-vm** and click on **Connect** to download the RDP file
* Open the RDP file to connect to the LABVM. Provide the credentials you received to login to the VM
* Once you login to the LABVM, server manager will open. Select Local Server and verify that IE Enhanced Security Configuration has also been turned off 
* User need a SSH client for connecting to a Linux Virtual Machine i.e. batch-jumpvm (follow Connect to Linux VM step)
* Verify that Azure Batch install on desktop
* Also verify that Microsoft Azure Storage Explorer is installed 

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided with Windows Server 2016 (x64)Microsoft and Ubuntu Server 16.04. FQDN of the LABVM virtual machine and administrator credentials are provided in the lab details page. You can remote into the virtual machine using the provided credentials

# Connect to Linux VM

* **Users can connect to the Linux VM using SSH Client**
* For SSH, If you are using a Windows machine, you would need a SSH client for connecting to a Linux Virtual Machine. Putty is the most widely used SSH client for windows. If you are using Mac or Linux based machines, you can use the bash terminal.
* If the user is accessing the Linux VM via putty, he will need to enable tunnelling to the local machine.

**Using SSH Client from your local machine:** 

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

# Known Issues


# Notes to Instructors / Proctors

* Windows-vm and batch-jumpbox is already deployed in **ODL_bigcompute-XXXXX-01** Resource Group and configured with all the requirements such as Microsoft Azure Storage Explorer, Azure CLI and Azure Batch Lab are already downloaded. 
* Users should **use** the **Azure Credentials** given to them to login to **Visual Studio**.

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
