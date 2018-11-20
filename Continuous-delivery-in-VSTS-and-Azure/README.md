# Introduction

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed. Also, for multi-day workshops, all virtual machines will be shutdown at 6.30 PM local time. On day 2, user should start the Virtual Machine from the lab activation page.

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

Also verify four resource groups **ODL-TailspinToys-41072-labvm**, **ODL-TailspinToys-41072-dev**, **ODL-TailspinToys-41072-test** and **ODL-TailspinToys-41072-production** already created. In resource group **ODL-TailspinToys-41072-labvm** you will get Azure Environment with the jumpvm deployed in it. **41072** in resource group names is unique ID, so don't be confuse if yours is different.

## Verify Virtual Machine

You are provided a [Visual Studio cummunity- Windows 2016](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.VisualStudioCommunity2017onWindowsServer2016x64?tab=Overview) with additional softwares configured with jumpvm named. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: jumpvm is provisioned in the resource group, in which you have reader role access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.</br></br>

## Notes to Attendees

# Known Issues

# Notes to Instructors / Proctors


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
