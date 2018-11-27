
# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Data Platform Upgrade and Migration](https://github.com/Microsoft/MCW-Data-Platform-upgrade-and-migration/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Data%20Platform%20upgrade%20and%20migration.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

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
 
# Verify the pre-provisioned Environment

1. Launch a browser using incognite or in-private mode, and navigate to [Microsoft Azure Portal](https://portal.azure.com). Once prompted, login with the Microsoft Azure credentials you received.   

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

# Notes to Instructors / Proctors:

* Users need not to perform any of the task in [Before Hands on Lab](https://github.com/Microsoft/MCW-Data-Platform-upgrade-and-migration/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Data%20Platform%20upgrade%20and%20migration.md#before-the-hands-on-lab) as it is pre-configured.
> For your information In [Task 5 (Before Hands on lab)](https://github.com/Microsoft/MCW-Data-Platform-upgrade-and-migration/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Data%20Platform%20upgrade%20and%20migration.md#task-5-add-inbound-port-1433-rule-on-the-sqlserverdw-vm-network-security-group): Add inbound port 1433 rule on the SqlServerDw VM, we are allowing all inbound  ports as needed. You can confirm this as shown in below screenshot.

![](Images/image1.png)


> Also in [Task 7 (Before Hands on Lab)](https://github.com/Microsoft/MCW-Data-Platform-upgrade-and-migration/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Data%20Platform%20upgrade%20and%20migration.md#task-7-open-port-1433-on-the-windows-firewall-of-the-sqlserverdw-vm): Open port 1433 on the Windows Firewall of the SqlServerDw VM.
 We already disabled the Windows Firewall inside the SqlServerDW VM as required. You can confirm this by opening Server Manager inside  VM. 
 
 ![](Images/image2.png)
 
 
 If its not disabled you can disable by clicking on Windows Firewall options as shown in below images:

 ![](Images/image3.png)
 


* For [Exercise 2 Task 2](https://github.com/Microsoft/MCW-Data-Platform-upgrade-and-migration/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Data%20Platform%20upgrade%20and%20migration.md#task-2-create-azure-database-migration-service) - **Create Azure Database MIgration Service**: Don't create Azure database migration service since it is pre-created in **ODL-data-platform-xxxxx-01** RG.


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.

  
