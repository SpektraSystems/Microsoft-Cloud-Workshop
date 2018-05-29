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
* Navigate to the resource group and view the already existing resources such as Container Service, build agent Linux VM, etc.
* Verify that following resources are predeployed in the resource group:
  1. Windows 2016 Virtual Machines named "labvm"


## Verify Azure Access

* Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You're provided one lab virtual machine running Windows Server 2016. You should be able to RDP(remote desktop) into VM with credentials available on lab details page. VM is preconfigured with Putty, Puttygen and Git Desktop


# Using Resource Groups
* You'd have three resource groups already provisioned for you, Please use these resource groups to create resources throughout the lab. You're not assigned permissions to create new RG, so if you get any permission error while creating resources, be sure sure to verify that you're choosing existing resource groups for deployment


# Notes to Instructors / Proctors

* All the tasks in Before Hands on Lab section is pre deployed.


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.


