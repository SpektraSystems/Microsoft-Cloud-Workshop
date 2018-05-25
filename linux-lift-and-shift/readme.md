
# Introduction

Linux Lift and Shift is a one day workshop lead by Microsoft or Microsoft partners. 
In this hands-on step-by-step lab, you will migrate an on-premises based helpdesk application called OsTicket to Azure.  This will be a two-phase project to lift and shift the application into Azure IaaS and then migrate it to Azure PaaS.  The application is Linux based using Apache, PHP and MySQL (LAMP).  During the process of these phases you will ensure zero data loss. 

*	Phase I:  Lift and shift the application from on-premises to Azure IaaS using an auto scaling Virtual Machine Scale Set and a MySQL cluster with 3 nodes.

*	Phase II: Migrate to PaaS using Azure App Services with a Linux Docker Container and Azure Database for MySQL.

 
# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
  
* Wait for the lab environment to be provisioned. Sometimes this can take upto **30 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed.
 
# Verify the pre-provisioned Environment

1. Launch a browser using incognite or in-private mode, and navigate to https://portal.azure.com. Once prompted, login with the Microsoft Azure credentials you received.   

2. Once you are logged in to the portal, navigate to Resource Groups. 
 
3. Note that you have access to five resource groups – ODL_lift-shift-xxxxx-01, ODL_lift-shift-xxxxx-02, ODL_lift-shift-xxxxx-03,  ODL_lift-shift-xxxxx-04 and ODL_lift-shift-xxxxx-05. Note: All these 5 resource groups has the pre-deployed environment. **User need not deploy any resource during the lab** 

4. Navigate to the resource group **ODL_lift-shift-xxxxx-01** and view the already existing resources such as LABVM Virtual Machine, Disk, etc

5. Using a remote desktop client, open a Remote Desktop Session into the LABVM using the labvmdnsname and credentials you received

6. Now check if MySQL Workbench is already installed


## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a Visual Studio Community 2017 on Windows Server 2016 (x64)Microsoft with MYSQL Workbench installed.FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials.

> Note: LAVVM is provisioned in the resource group **ODL_lift-shift-xxxxx-01**. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.


# Known Issues

> **Possible Solutions**:

* With the release of the March 2018 Security bulletin, there was a fix that addressed a CredSSP, “Remote Code Execution” vulnerability (CVE-2018-0886) which could impact RDP connections. 
**Resolution**
Please follow the instruction under https://github.com/SpektraSystems/Microsoft-Cloud-Workshop/blob/master/RDP%20CredSSP/README.md

# Notes to Instructors / Proctors

* For Exercise 1, users should navigate to the **ODL_lift-shift-xxxxx-02** resource group and use the already deployed resources

* For Exercise 2 Task 1 and 2, users should use the **ODL_lift-shift-xxxxx-03** resource group and use the already deployed resources

* For Exercise 2 Task 3, 4 and 5, users should use the **ODL_lift-shift-xxxxx-04** resource group and use the already deployed resources

* For Exercise 3, users should use the **ODL_lift-shift-xxxxx-05** resource group and use the already deployed resources


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.

  
