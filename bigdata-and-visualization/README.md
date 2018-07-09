# Introduction

In this workshop, you will complete a web app using Machine Learning to predict travel delays given flight delay data and weather conditions, plan the bulk data import operation, followed by preparation tasks, such as cleaning and manipulating the data for testing, and training your Machine Learning model. You can find details about the worksohp [here](https://spektraazurelabs.blob.core.windows.net/bigdata-visualization/Hands-on lab step-by step - Big data and visualization-updated.docx).</br></br>

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.
 
* On the next page, click the **Launch Lab** button.
  
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
  
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed.</br></br>

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided. In Azure portal you can navigate to the Resource groups to see the pre-deployed Resource group.
* You should use the existing Resource group during the lab.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Data Science Virtual Machine

You are provided a [Data Science Virtual Machine - Windows 2016](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/microsoft-ads.windows-data-science-vm) with additional softwares configured. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: DSVM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

## Verify the pre-requisite Azure resources
1. **Machine Learning Studio Workspace** is provisioned in the resource group, in which you have access.
2. **Azure HDInsight Cluster** : Refer registration page/email for cluster credentials and cluster ssh credentials. .  
3. **Virtual Network**
4. **Public IP**
5. **Network Interface**
6. **Load Balancer**
7. **Storage accounts**
8. **Azure DataBricks**
9. **Data Factory**
10. **Machine Learning Experimentation**
11. **Machine Learning Model Management**


## Notes to Attendees
While doing **Before the Hands-on-lab** section, follow the below steps.
1. You need not to execute **Task 1** in **Before the Hands-on-lab** section, since it is pre-created. You can use the pre-created resources during the lab.
2. You should perform **Task 2**. In this task, you will **register for a trial API account at WeatherUnderground.com**
3. Don’t deploy **Azure Databricks** specified in **Task 3**, since it is pre-created.
4. Don’t install **PowerBi Desktop** specified in **Task 4**, since it’s preinstalled in DSVM.
5. You should perform **Task 4 and Task 5** in which you will create a blob storage and retrieve **Azure Storage information** and **Create container**.
6. Don’t deploy **Data Factory** specified in **Task 6**, since it is pre-created.
7. In **Task 8** Users should open **pre-created** **Machine Learning Experimentation** account and **assign owner** for the workspace *For more details please go through **Known Issues**.

# Known Issues
### Connecting DSVM with RDP having issue addresses CredSSP

> **Possible Solutions**:

* With the release of the March 2018 Security bulletin, there was a fix that addressed a CredSSP, “Remote Code Execution” vulnerability (CVE-2018-0886) which could impact RDP connections. 
**Resolution**
Please follow the instruction under https://github.com/SpektraSystems/Microsoft-Cloud-Workshop/blob/master/RDP%20CredSSP/README.md

**For Task 8** Please follow below steps to assign owner to the workspace.
 
 **Step 1**. Open **Machine Learning Experimentation** account which is pre- created.

  ![](images/VirtualMachines1.png)
 
 **Step 2** Click on **Add Workspace** under Application Settings.
  ![](images/VirtualMachines1.png)
  
 **Step 3** Enter the **workspace name**, **assign owner** to workspace and click on **Create workspace**.
   [](images/VirtualMachines1.png)

# After the hands-on lab 
Duration: 10 minutes</br></br>
In this exercise, attendees will deprovision any Azure resources that were created in support of the lab.
## Task 1: Delete resource group
1.	Using the Azure portal, navigate to the Resource group you used throughout this hands-on lab by selecting Resource groups in the left menu.</br>
2.	Search for the name of your research group and select it from the list.</br>
3.	Select Delete in the command bar and confirm the deletion by re-typing the Resource group name and selecting Delete.</br>
You should follow all steps provided after attending the Hands-on lab.</br></br>

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.


