
# Introduction

In data platform upgrade and migration workshop, you will gain a better understanding of how to conduct a site analysis for a customer to compare cost, performance, and level of effort required to migrate from Oracle to SQL Server. You will evaluate the dependent applications and reports that will need to be updated and come up with a migration plan. In addition, you will design and build a proof of concept (POC) and help the customer take advantage of new SQL Server features to improve performance and resiliency, as well as explore ways to migrate from an old version of SQL Server, to the latest version and consider the impact of migrating from on-premises to the cloud.

At the end of this workshop, you will be better able to conduct a site analysis for compare cost, performance, and level of effort required to migrate from Oracle to SQL Server.

# Azure services and related products
* Azure App Services
* Azure Database Migration Service (DMS)
* Azure SQL Database
* Azure SQL Data Warehouse
* Data Migration Assistant (DMA)
* SQL Server 2008 R2 and 2017
* SQL Server Management Studio (SSMS)
* SQL Server Migration Assistant (SSMA)
* Visual Studio 2017

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
  
* Wait for the lab environment to be provisioned. Sometimes this can take upto **30 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed.
 
# Verify the pre-provisioned Environment

1. Launch a browser using incognite or in-private mode, and navigate to https://portal.azure.com. Once prompted, login with the Microsoft Azure credentials you received.   

2. Once you are logged in to the portal, navigate to Resource Groups. 
 
3. Note that you have access to two resource groups – **ODL-data-platform-xxxxx-01**, **ODL-data-platform-xxxxx-sqlVm**. Note: These two resource groups has the pre-deployed environment. 

4. Navigate to the resource group **ODL-data-platform-xxxxx-01** and view the already existing resources such as **LABVM** Virtual Machine, Disk, SQL database **WorldWideImporters**, Azure database migration service (DMS)**wwi-dms** etc.

5. Navigate to the resource group **ODL-data-platform-xxxxx-sqlVm** and view the already existing resources such as **SqlServerDw** Virtual Machine, Disk, Vnet etc.


## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machines

You are provided a **Visual Studio Community 2017 on Windows Server 2016 (x64)Microsoft(LABVM)** and **Windows Server 2012 R2 Data center(SqlServerDw)**.FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials.

> Note: LAB VM is provisioned in the resource group **ODL-data-platform-xxxxx-01**. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

> Note: SqlServerDW VM is provisioned in the resource group **ODL-data-platform-xxxxx-sqlVM**. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

# Known Issues

> **Possible Solutions**:

* With the release of the March 2018 Security bulletin, there was a fix that addressed a CredSSP, “Remote Code Execution” vulnerability (CVE-2018-0886) which could impact RDP connections. 
**Resolution**
Please follow the instruction under https://github.com/SpektraSystems/Microsoft-Cloud-Workshop/blob/master/RDP%20CredSSP/README.md

# Notes to Instructors / Proctors:

* For Exercise 2 Task 2 - **Create Azure Database MIgration Service**: Don't create Azure database migration service since it is pre-created in **ODL-data-platform-xxxxx-01** RG.

* For **Exercise 4** Setup **Oracle 11g Express Edition** Task 1 Install Oracle XE, please follow below link to download Oracle Express Edition for Windows:

LINK: https://www.oracle.com/technetwork/database/database-technologies/express-edition/downloads/xe-prior-releases-5172097.html 

Then you need to accept the license agreement, and select Oracle Database 11gR2 Express Edition for Windows x32

  ![](oracle1/securityimage1.png)


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.

  
