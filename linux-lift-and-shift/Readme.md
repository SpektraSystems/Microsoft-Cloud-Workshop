
# Introduction
This is a supplement guide to ‘Microsoft Cloud Workshop - [Linux Lift and Shift](https://github.com/Microsoft/MCW-Linux-lift-and-shift/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Linux%20lift%20and%20shift.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

Linux Lift and Shift is a one day workshop lead by Microsoft or Microsoft partners. 
In this hands-on step-by-step lab, you will migrate an on-premises based helpdesk application called OsTicket to Azure.  This will be a two-phase project to lift and shift the application into Azure IaaS and then migrate it to Azure PaaS.  The application is Linux based using Apache, PHP and MySQL (LAMP).  During the process of these phases you will ensure zero data loss. 

*	Phase I:  Lift and shift the application from on-premises to Azure IaaS using an auto scaling Virtual Machine Scale Set and a MySQL cluster with 3 nodes.

*	Phase II: Migrate to PaaS using Azure App Services with a Linux Docker Container and Azure Database for MySQL.
 
# Verify the pre-provisioned Environment

1. Launch a browser using incognite or in-private mode, and navigate to [Microsoft Azure Portal](https://portal.azure.com). Once prompted, login with the Microsoft Azure credentials you received.   

2. Once you are logged in to the portal, navigate to Resource Groups. 
 
3. Note that you have access to five resource groups – ODL_lift-shift-xxxxx-OPSLABRG, ODL_lift-shift-xxxxx-OsTicketOnPrem, ODL_lift-shift-xxxxx-OsTicketMySQLVM,  ODL_lift-shift-xxxxx-OsTicketVMSSRG and ODL_lift-shift-xxxxx-OsTicketPaaSRG. Note: All these 5 resource groups has the pre-deployed environment. **User need not deploy any resource during the lab** 

4. Navigate to the resource group **ODL_lift-shift-xxxxx-OPSLABRG** and view the already existing resources such as LABVM Virtual Machine, Disk, etc

5. Using a remote desktop client, open a Remote Desktop Session into the LABVM using the labvmdnsname and credentials you received

6. Now check if MySQL Workbench is already installed


## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a Visual Studio Community 2017 on Windows Server 2016 (x64)Microsoft with MYSQL Workbench installed.FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials.

> Note: LAB VM is provisioned in the resource group **ODL_lift-shift-xxxxx-OPSLABRG**. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.


# Known Issues


# Notes to Instructors / Proctors

* For Exercise 1, users should navigate to the **ODL_lift-shift-xxxxx-OsTicketOnPrem** resource group and use the already deployed resources

* For Exercise 2 Task 1 and 2, users should use the **ODL_lift-shift-xxxxx-OsTicketMySQLVM** resource group and use the already deployed resources

* For Exercise 2 Task 3, 4 and 5, users should use the **ODL_lift-shift-xxxxx-OsTicketVMSSRG** resource group and use the already deployed resources

* For Exercise 3, users should use the **ODL_lift-shift-xxxxx-OsTicketPaaSRG** resource group and use the already deployed resources


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.

  
