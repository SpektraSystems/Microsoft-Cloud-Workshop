# Introduction

The scenario will challenge you to setup continuous integration and delivery of an application using open source tools such as Jenkins and GitHub along with automated deployments to Azure App Services. You will learn about continuous deployment and the benefits of staged publishing.

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
* Navigate to the resource group and view the already existing resources such as Linux VM, etc.
* Verify that following resources are predeployed in the resource group:
  1. Ubuntu Server 16.04 from Canonical named "labvm"


## Verify Azure Access

* Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Using Resource Groups
* You'd have two resource groups already provisioned for you, Please use these resource groups to create resources throughout the lab. You're not assigned permissions to create new RG, so if you get any permission error while creating resources, be sure sure to verify that you're choosing existing resource groups for deployment

## Verify Virtual Machine

1. **LabVM** 
  OS: Ubuntu Server 16.04 from Canonical
  You can RDP into this VM using the credentials and FQDN provided in the Lab details page.
  Verify Visual Studio Code is installed.Also verify that you can RDP into the virtual machine if you wants to directly RDP to the Linux VM,FQDN of the virtual machine and administrator credentials are provided in the lab details page.

2. **jenkins** (Ubuntu Server 16.04 from Canonical) is pre-provisioned with additional tools configured.

## Connect to VMs

1. **Using RDP Client on your local machine for labvm:**

    1.	Using the RDP Client, Login in to the Lab VM using environment credentials you received.

2. **Using SSH Client on your local machine for jenkins vm** 
 
   * **If you are using Git Bash**
  
    1. Use the following command to SSH into the jenkins VM
    
       ssh -L 127.0.0.1:8080:localhost:8080 jenkinsadmin@[jenkinsvm-dns]

   * **If you are using Putty to connect** 

    1.	Login into the jenkins and open putty.exe from the Desktop.

    2.	An application window pops up when user run putty.exe.

    3.	Enter the jenkinsVMDnsName of the VM to the Host Name (or IP address) box of the putty. Port will be 22 by default.

    4.	Go to the Tunnels section in PuTTY, 
 
    5.	Now, user will configure a specific Local port 8080, that will redirect to 8001 of the build agent Linux VM. 

    6.	Provide the following details and click on Add:
       Source Port: 8080
       Destination: 127.0.0.1:8080
       Then Click on Open.
 
    7.	Now a new terminal will pop and user will be connected to the build agent virtual machine.

    8.	The PuTTY Security Alert will pop up. Click on Yes.

    9.	Login using the adminUsername and adminPassword for the jenkins VM.
 
    10.	After entering the username and password user can start accessing the jenkins Linux VM.
 
 ## Known Issues
 
 In Exercise 3>Task 3>Step 10:For building the docker image, Oprn a bash shell and run the command **sudo su -**. You have to run the command **visudo**.Add demouser configuration  in file.Run the **exit** command.After that you have to restart your VM and build the image.
    
## Notes to Instructors / Proctors

* All the tasks in Before Hands on Lab section is pre deployed.

## Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
