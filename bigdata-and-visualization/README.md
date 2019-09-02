# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Bigdata and Visualization](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Big%20data%20and%20visualization.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

In this workshop, you will complete a web app using Machine Learning to predict travel delays given flight delay data and weather conditions, plan the bulk data import operation, followed by preparation tasks, such as cleaning and manipulating the data for testing, and training your Machine Learning model.

# Azure services and related products
* Azure Databricks
* Azure Machine Learning services
* Azure Data Factory (ADF)
* Azure Storage
* Power BI Desktop
* Azure App Service

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided. In Azure portal you can navigate to the Resource groups to see the pre-deployed Resource group.
* You should use the existing Resource group during the lab.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Data Science Virtual Machine

You are provided a [Data Science Virtual Machine - Windows 2016](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/microsoft-ads.windows-data-science-vm) with additional softwares configured. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: DSVM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

## Verify the pre-requisite Azure resources
1. **Data Sceince Virtual Machine**
2. **Virtual Network**
3. **Public IP**
4. **Network Interface**
5. **Storage accounts**
6. **Data Factory**


## Notes to Attendees
While doing [Before the Hands-on-lab](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#before-the-hands-on-lab) section, follow the below steps.
1. You need not to execute [Task 1](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-1-deploy-data-science-virtual-machine-cluster-to-azure) in **Before the Hands-on-lab** section, since it is pre-created. You can use the pre-created resources during the lab.
2. You should perform [Task 2](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-2-register-for-a-trial-api-account-at-darkskynet) In this task, you will **register for a trial API account at WeatherUnderground.com**
3. You should perform [Task 3](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-3-provision-azure-databricks), [Task 4](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-4-create-azure-storage-account), [Task 5](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-5-retrieve-azure-storage-account-information-and-create-container) for Retrieve Azure Storage account information and create container, etc.
4. Don’t deploy **Data Factory** specified in [Task 6](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-6-provision-azure-data-factory), since it is pre-created.
5. You should perform [Task 7](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-7-initialize-azure-machine-learning-workbench-on-the-lab-dsvm): Initialize Azure Machine Learning Workbench on the Lab DSVM.
   Need not to download Machine learning Workbench as it is pre-downloaded. You can find the setup of workbench on downloads folder at  desktop.
6. You should perform [Task 8](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-8-provision-azure-machine-learning-experimentation-service): Provision Azure Machine Learning Experimentation service
7. You should perform [Task 9](https://github.com/Microsoft/MCW-Big-data-and-visualization/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Big%20data%20and%20visualization.md#task-9-create-an-azure-databricks-cluster): Create an Azure Databricks cluster

# Known Issues

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.


