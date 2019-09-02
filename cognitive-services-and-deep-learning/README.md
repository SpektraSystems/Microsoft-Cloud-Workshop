# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Cognitive Services and Deep Learning](https://github.com/Microsoft/MCW-Cognitive-services-and-deep-learning/blob/master/Hands-on%20lab/HOL%20step-by%20step%20-%20Cognitive%20services%20and%20deep%20learning.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Pre-requisite Azure Resources

You are provided a Data Science Virtual Machine - Windows 2016 with additional softwares configured in advance. FQDN of the virtual machine and administrator credentials are provided in the lab details page.You can remote into the virutal machine using the provided credentials. Please use this VM during the lab instead of create new VM as specified in Task-1.


# Known Issues
* In **Exercise 1**, Task 1 -> Step 3 search for **Machine Learning Experimentation** and select **Machine Learning Experimentation (Retiring)** from the list that appears because **Machine Learning Experimentation (preview)** is updated with **Machine Learning Experimentation (Retiring)** in Azure Portal.

* In **Exercise 2**, task 1 you need to edit the command for creating the cluster environment to specify using existing resource group which is pre-created for you, otherwise the deployment would fail. Make a note of name of your existing resource group and include in the command as specified below
```
az ml env setup -c -g <resource group> -n mcwailabenv --location eastus2
```

# Notes to Instructors / Proctors

* LABVM is already deployed in ODL_csdl-XXXXX Resource Group and configured with all the requirements.
* Installation of AzureML Workbench Setup will take around 30-45 minutes to install.

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.



