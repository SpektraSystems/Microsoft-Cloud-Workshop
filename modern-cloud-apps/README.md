# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Modern Cloud Apps](https://github.com/Microsoft/MCW-Modern-cloud-apps/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Modern%20cloud%20apps.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com
well as in the browser.

# Verify the pre-provisioned Environment

* Users can use the **Azure Credentials** given to them to login to the Azure Portal
* Two resource groups **ODL_mca-XXXXX-01** and **ODL_mca-XXXXX-contososports** will be already created. In resource group **ODL_mca-XXXXX-01** you will get Azure Environment with the LABVM deployed in it.
* Users can select **labvm** and click on **Connect** to download the RDP file
* Open the RDP file to connect to the LABVM. Provide the credentials you received to login to the VM
* Once you login to the LABVM, server manager will open. Select Local Server and verify that IE Enhanced Security Configuration has also been turned off 
* Go to C:\MCW folder and verify application files are there such as:
```
Contoso.Apps.SportsLeague.Web 
Contoso.Apps.SportsLeague.Admin 
Contoso.Apps.SportsLeague.Data 
Contoso.Apps.SportsLeague.Offers 
Contoso.Apps.PaymentGateway 
```
* Also verify that SQL Server Management Studio is installed 

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a Visual Studio Community 2017 on Windows Server 2016 (x64)Microsoft with additional softwares configured. FQDN of the LABVM virtual machine and administrator credentials are provided in the lab details page. You can remote into the virtual machine using the provided credentials

# Notes to Attendees
You can use **ODL_mca-XXXXX-contososports** resource group for deploying all the resources in this lab.</br>

# Known Issues

### Issue with Order Checkout

* You may find the following error message after clicking the Continue button on the Order Checkout page.
```
"Something went wrong...
Uh, oh! Something happened, and it might have been my fault...
Here are some potentially helpful details about what went wrong:
You must write ContentLength bytes to the request stream before calling [Begin]GetResponse..
```
> **Possible Solutions**: </br>
* It's due to TLS 1.0, 1.1 reaching EOL. Modify the code as follows in /Helpers/PaymentGatewayFunctions.cs:

        string strPost = NvpRequest + "&" + buildCredentialsNVPString();
        // add the following line to force TLS1.2
        ServicePointManager.SecurityProtocol = SecurityProtocolType.Tls12;
        HttpWebRequest objRequest = (HttpWebRequest)WebRequest.Create(url);
# Notes to Instructors / Proctors

* LABVM is already deployed in **ODL_mca-XXXXX-01** Resource Group. LABVM is configured with all the requirements such as Application Files which is already downloaded in C:\MCW and SQL Server Management Studio.
* Users should **use** the **Azure Credentials** given to them to login to **Visual Studio**.

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
