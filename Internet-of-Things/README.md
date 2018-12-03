# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Internet of Things](https://github.com/Microsoft/MCW-Internet-of-Things/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Internet%20of%20Things.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

The scenario will challenge you to setup continuous integration and delivery of an application using open source tools such as Jenkins and GitHub along with automated deployments to Azure App Services. You will learn about continuous deployment and the benefits of staged publishing.

# Verify the pre-provisioned Environment

* Open a browser instance in InPrivate / incognito mode and navigate to https://portal.azure.com 
* Login to the portal using Azure Credentials issued for your environment.  
* Once you are logged in to the portal, navigate to Resource Groups. 
* Note that you have access to 1 resource group  


## Verify Azure Access

* Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You're provided one lab virtual machine running Visual Studio Community 2017 on Windows Server 2016 (x64). You should be able to RDP(remote desktop) into VM with credentials available on lab details page.


# Verify pre-requisite resources
* You'd have one resource groups already provisioned for you, Please use these resource groups to create resources throughout the lab. You're not assigned permissions to create new RG, so if you get any permission error while creating resources, be sure to verify that you're choosing existing resource groups for deployment.
* Navigate to the resource group and view the already existing resources such as virtual machine,OS Disk,Public IP etc. You cannot deploy anything in this resource group.

# Notes to Attendees
You can access powerBI with the same credentials that used for Azure login.
    
# Known Issues
### Getting Path error
> Possible Solution
In Exercise 4 > Task 4 > Step 17, you may find a path error while running the command.
For solving this issue, you may have to run the following command instead of the given command.
```
# Create a Dataframe containing data from all the files in blob storage, regardless of the folder they are located within.
df = spark.read.options(header='true', inferSchema='true').csv("dbfs:/mnt/smartmeters/*/*/*/*/*.csv",header=True)
print(df.dtypes)
```
# Notes to Instructors / Proctors

* All the tasks in Before Hands on Lab section is pre deployed.


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.


