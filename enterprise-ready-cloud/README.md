# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Enterprise Ready Cloud](https://github.com/Microsoft/MCW-Enterprise-ready-cloud/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Enterprise-ready%20cloud.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

In the Enterprise Ready Cloud workshop, attendees will learn how to use Azure RBAC and Policy to help control usage within an Azure subscription, or across subscriptions using Management Groups. They will also learn how to use DevTest Labs, including setting up VPN access to the test environment.

# Verify the pre-provisioned Environment

## Verify Azure Access
Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / Edge or Incognito mode of Chrome browser.

Also verify resource group **ODL-erc-41071** already created. In resource group **ODL-erc-41071** you will get Azure Environment with the **lab-vm** deployed in it. **41071**  is unique ID, so don't be confused if yours is different.

## Verify Virtual Machine
You are provided a [Visual Studio cummunity- Windows 2016](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.VisualStudioCommunity2017onWindowsServer2016x64?tab=Overview) with additional softwares configured with lab-vm named. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: lab-vm is provisioned in the resource group **ODL-erc-41071**. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

# Known Issues
# Notes to attendees 
     
1. After completing the lab. Move the subscription from **Enterprise Ready Cloud** group to **Tenant Root Group** and then delete **Enterprise Ready Cloud** group.          
            
# Notes to Instructors / Proctors


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
