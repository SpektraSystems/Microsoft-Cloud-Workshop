# Introduction

This is a supplement guide to  ‘[Microsoft Cloud Workshop - OSS Devops](https://github.com/Microsoft/MCW-OSS-DevOps/tree/master/Hands-on%20lab)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com.

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **30 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed.

# Verify the pre-provisioned Environment

* Open a browser instance in InPrivate / incognito mode and navigate to https://portal.azure.com 
* Login to the portal using Azure Credentials issued for your environment.  
* Once you are logged in to the portal, navigate to Resource Groups. 
* Note that you have access to 3 resource group  


## Verify Azure Access

* Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You're provided one lab virtual machine running Visual Studio Community 2017 on Windows Server 2016 (x64). You should be able to RDP(remote desktop) into VM with credentials available on lab details page.


# Verify pre-requisite resources
* You'd have three resource groups already provisioned for you, Please use these resource groups to create resources throughout the lab. You're not assigned permissions to create new RG, so if you get any permission error while creating resources, be sure to verify that you're choosing existing resource groups for deployment
* Navigate to the resource group named ODL-xxx-OPSLABRG and view the already existing resources such as virtual machine,OS Disk,Public IP etc.
* Verify that remaining resource groups are empty.

# Notes to Attendees
While doing Exercise 1, please follow the below steps.
* In Task 1 > Step 1 after selecting Bash, In the Storage mounting page, Select "Show Advanced Settings". In the next page provide the following datails.
    * Resource group : Click on *use existing* and select resource group named as ODL-xxx-OsTicketPaaSRG.
    * Storage account name : Provide any unique name.
    * File share : Provide any unique name.
    * Click on *Create Storage*
   
* You can skip Task 1 > Step 2, since all resource groups are pre-created. 
* In Task 1 > Steps 3&4, provide our pre-created resource group name(ODL-xxx-OsTicketPaaSRG) in the command.
* In Task 3 > Steps 3&4, provide our pre-created resource group name(ODL-xxx-OsTicketPaaSRG) in the command.
* In Task 5, for getting Deployment credentials page,Open the Web app and navigate through Deployment Center > FTP > Dashboard > User Credentials.</br></br> 
While doing Exercise 3, please follow the below steps.
* In Task 1, while creating Jenkins you can use the pre-deployed reource group - ODL-xxx-JenkinsRG.
* You can skip Task 4 and Task 5, because GitHub services are deprecated.
    
# Known Issues

# Notes to Instructors / Proctors

* All the tasks in Before Hands on Lab section is pre deployed.


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.


