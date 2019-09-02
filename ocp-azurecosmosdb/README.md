# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [OCP Azure CosmosDB](https://cosmosdb.github.io/labs/) to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

This series of workshops will give you hands-on experience working with Azure Cosmos DB using the SQL API, JavaScript and .NET Core SDK.

# Verify the pre-provisioned Environment

* Open a browser instance in InPrivate / incognito mode and navigate to https://portal.azure.com 
* Login to the portal using Azure Credentials issued for your environment.  
* Once you are logged in to the portal, navigate to Resource Groups. 
* Note that you have access to one resource group - **ODL-cosmosdb-XXXXX-01** has the pre-deployed environment. 
    >Note: For all tasks which involve deployment, use **ODL-cosmosdb-XXXXX-01**
  
* Navigate to the resource group and view the already existing resources such as Azure CosmosDB, LABVM Virtual Machine, Disk, IP Address, etc.
* Using a remote desktop client, open a Remote Desktop Session into the LABVM using the labvmdnsname and credentials you received

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

 **Windows LabVM** 
  OS: Visual Studio CE 2017 on Windows Server 2016
  You can RDP into this VM using the credentials and FQDN provided in the Lab details page.
  Verify that Git Bash and Putty is there in the Desktop, and Visual Studio Code is installed.

# Known Issues

You will not be able to open the project folder in Visual Studio code according to the Lab Guide, so please follow the steps below to open the project folder in the Visual Studio code. :

1. Search for Visual Studio Code from start **Menu** :<br/>
<img src="images/visual.jpg"/><br/>

2. Click on **Open Folder** then select the project folder and open it. <br/>
<img src="images/visual1.jpg"/><br/>

# Notes to Instructors / Proctors

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
