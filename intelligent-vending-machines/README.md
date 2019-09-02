# Introduction
This is a supplement guide to ‘Microsoft Cloud Workshop - [Intelligent Vending Machines](https://github.com/Microsoft/MCW-Intelligent-vending-machines/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Intelligent%20vending%20machines.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

In this workshop, attendees will implement an IoT solution for intelligent vending machines, leveraging facial feature recognition and Azure Machine Learning, to gain a better understanding of building cloud-based machine learning app, and real-time analytics with SQL Database in-memory and columnar indexing. </br></br>

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.In Azure portal you can navigate to the Resource groups to see the pre-deployed Resource group.
* You should use the existing Resource group during the lab.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a [Data Science Virtual Machine - Windows 2016](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/microsoft-ads.windows-data-science-vm) with additional softwares configured. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: DSVM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

You are also provided a **Microsoft Machine Learning Server 9.3.0 on Ubuntu 16.04** VM running Microsoft Machine Learning Server. You will use this machine to host the R Server Operationalization service.

## Verify the pre-requisite Azure resources
Following azure resources are created for you in advance, Please use them instead of creating more resources. 
1. **SQL Database** 
2. **SQL Server** 
3. **Azure HDInsight Cluster**   
4. **Virtual Network**
5. **Public IP**
6. **Network Interface**
7. **Storage accounts**

## Notes to Attendees
* While doing **Before hand-on-lab** section, follow the below mentioned steps.
1. You need not to execute **Task 1, Task 2**, **Task 3** and **Task 4**. All the resources in these tasks are pre-created (R Server with HDInsight Spark, Lab Virtual Machine and PowerBI Desktop installed on Lab Virtual Machine).
2. In **Task 5**, you need to do **Step 8** to **Step 13**. You can skip all other steps in this task because SSH Client is pre-installed.
3. You can skip **Task 6**.</br></br>

# Known Issues
### Failure while running the following command:

### Not able to see "Take Picture" option:
(Exercise 2 > Task 6 > step 7)
> **Possible Solutions**:

 * Try maximizing and minimizing the window , you can see the part of that "**Take Picture**" option at the bottom of the window.</br></br>

# Notes to Instructors / Proctors
* Attendees need not to deploy any Azure resources except a Storage account creating in Exercise 1 > Task 4. All other Azure resources are automated and attendees can use those resources during the workshop.
* Attendees can refer **Registration Page/Email** for all details of the resources deployed. </br></br>

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.



