# Introduction

In this workshop, attendees will implement three different environments and use Azure BCDR technologies to achieve three distinct goals for each environment type.  These will include a migration to Azure, Azure region to region failover using Azure Site Recovery (ASR) and a PaaS implementation using BCDR technologies to ensure high availably of an application.

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed. Also, for multi-day workshops, all virtual machines will be shutdown at 7 PM local time and start at 8AM local time.

# Verify the pre-provisioned Environment

* Users can use the **Azure Credentials** given to them to login to the Azure Portal
* Resource Group **ODL_bcdr-XXXXX-01** will be already created in the Users Azure Environment with the LABVM deployed in it.
* **LABVM** has been configured with the following:
  1. IE Enhanced Security has been disabled
  2. SQL Server Express 2017
  3. SQL Server Management Studio 2017
  4. Student files are downloaded into C:\HOL Directory
* Users can select **LABVM** and click on **Connect** to download the RDP file
* Open the RDP file to connect to the LABVM. Provide the credentials you received to login to the VM
* Once you login to the LABVM, server manager will open. Select Local Server and verify that IE Enhanced Security Configuration has also been turned off
* Now go to C:\HOL directory and verify the student files are there
* Also verify that SQL Server Express 2017 as well as SQL Server Management Studio is installed 

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a Visual Studio Community 2017 on Windows Server 2016 (x64)Microsoft with additional softwares configured. FQDN of the LABVM virtual machine and administrator credentials are provided in the lab details page. You can remote into the virtual machine using the provided credentials.

# Known IssueS

# Notes to Instructors / Proctors
* User need to perform only creation of Resource Groups task in Before Hands on Lab 
* Users should **use** the **Azure Credentials** given to them to login to **Visual Studio**

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.



