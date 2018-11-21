# Introduction

This is a supplement guide to  ‘Microsoft Cloud Workshop - [Continuous-delivery-in-VSTS-and-Azure](https://github.com/Microsoft/MCW-Continuous-delivery-in-VSTS-and-Azure/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Continuous%20delivery%20in%20VSTS%20and%20Azure.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

Also verify four resource groups **ODL-TailspinToys-41072-labvm**, **ODL-TailspinToys-41072-dev**, **ODL-TailspinToys-41072-test** and **ODL-TailspinToys-41072-production** already created. In resource group **ODL-TailspinToys-41072-labvm** you will get Azure Environment with the jumpvm deployed in it. **41072** in resource group names is unique ID, so don't be confuse if yours is different.

## Verify Virtual Machine

You are provided a [Visual Studio cummunity- Windows 2016](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.VisualStudioCommunity2017onWindowsServer2016x64?tab=Overview) with additional softwares configured with jumpvm named. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: jumpvm is provisioned in the resource group, in which you have reader role access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.</br></br>

## Notes to Attendees

1. You will get four Resource Groups **ODL-TailspinToys-41072-labvm**, **ODL-TailspinToys-41072-dev**, **ODL-TailspinToys-41072-test** and **ODL-TailspinToys-41072-production** already created.
1. Please use **ODL-TailspinToys-41072-dev** instead of **TailspinToys-dev**, **ODL-TailspinToys-41072-test** instead of **TailspinToys-test** and **ODL-TailspinToys-41072-production** instead of **ODL-TailspinToys-41072-production** to deploy TailspinToys project template.
1. When you will login to http://visualstudio.com in [Exercise 2](https://github.com/Microsoft/MCW-Continuous-delivery-in-VSTS-and-Azure/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Continuous%20delivery%20in%20VSTS%20and%20Azure.md#exercise-2-create-visual-studio-team-services-team-project-and-git-repository). After creating TailspinToys project you will get different UI, not as shown in lab guide. So you need to turn off all preview features of VSTS.
    - Click on the user profile section in upper right corner
      

# Known Issues

# Notes to Instructors / Proctors


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
