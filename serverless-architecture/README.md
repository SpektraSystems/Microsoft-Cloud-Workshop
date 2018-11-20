# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Serverless Architecture](https://github.com/Microsoft/MCW-Serverless-architecture/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Serverless%20architecture.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

Also verify two resource groups **ODL_serverless-architecture-XXXXX-01** and **ODL_serverless-architecture-XXXXX-02** already created. In resource group **ODL_serverless-architecture-XXXXX-01** you will get Azure Environment with the LABVM deployed in it

## Verify Virtual Machine

You are provided a [Visual Studio cummunity- Windows 2016](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.VisualStudioCommunity2017onWindowsServer2016x64?tab=Overview) with additional softwares configured with jumpvm named. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: jumpvm is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.</br></br>


## Notes to Attendees
While doing **Before the Hands-on-lab** section, follow the below steps.
1. You can skip **Task 1** in **Before the Hands-on-lab** section, since it is pre-created. You can use the pre-created resources during the lab.
2. You should perform **Task 3, Task 4 and Task 5**.
3. You can skip **Task 6**, since the required resource groups are pre-created. You should create all the resource for the lab in **ODL_serverless-architecture-XXXXX-02** resource group.
4. When you deploy **Function App** in exercise 1 - task 2. Choose **Java Script** instead of .net in RunTime Stack
<kbd>![](images/functionapp.jpg "Function App")</kbd>
5. In Exercise 2- task 1 step 4, configure **computerVisionApiUrl** as **https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/ocr**. Here just modify the endpoint(https://australiaeast.api.cognitive.microsoft.com/) of your computer vision endpoint url.
# Known Issues

### Not showing Telemetry data in sample Telemetry under App Insight, Lab guide page number: 55 and further steps of App Insight.
Please re-verify previous steps of lab, most likely you missed some configuration part.


# Notes to Instructors / Proctors


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
