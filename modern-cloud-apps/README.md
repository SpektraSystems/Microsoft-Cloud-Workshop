# Introduction

This is a supplement guide to  ‘[Microsoft Cloud Workshop - Modern Cloud Apps](https://github.com/Microsoft/MCW-Modern-cloud-apps/tree/master/Hands-on%20lab)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed.

# Verify the pre-provisioned Environment

* Users can use the **Azure Credentials** given to them to login to the Azure Portal
* Two resource groups **ODL_mca-XXXXX-01** and **ODL_mca-XXXXX-contososports** will be already created. In resource group **ODL_mca-XXXXX-01** you will get Azure Environment with the LABVM deployed in it.
* Users can select **labvm** and click on **Connect** to download the RDP file
* Open the RDP file to connect to the LABVM. Provide the credentials you received to login to the VM
* Once you login to the LABVM, server manager will open. Select Local Server and verify that IE Enhanced Security Configuration has also been turned off 
* Go to C:\Hackathon folder and verify application files are there such as:
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
While doing Exersice 4, please follow the below steps.
* In Task 1 > Subtask 2, instead of Steps 3, 4 & 5, do the following:
    * In **Usage** menu click on **Impact**.
    * In the new page that appear, click on **Get Started**.
    * Copy the full contents of the JavaScript.
    * Continue with Step 6.</br>
* You can skip Exercise 5.

# Known Issues

### Issue while Configuring Cross-Origin Resource Sharing (CORS)

> **Possible Solutions**:

* In Exercise 1 > Task 5 > Subtask 2 > step 2, instead of URL of the Offers Web API App, you shoule provide URL of the ContosoSports Web App.
### Issues with Exercise 5

> **Possible Solutions**:

* You can skip exercise 5, since it is not updated according to the updated Azure portal.

# Notes to Instructors / Proctors

* LABVM is already deployed in **ODL_bcdr-XXXXX-01** Resource Group and configured with all the requirements such as SQL Server Management Studio and Application Files are already downloaded into the VM in C:\Hackathon. 
* Users should **use** the **Azure Credentials** given to them to login to **Visual Studio**.

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
