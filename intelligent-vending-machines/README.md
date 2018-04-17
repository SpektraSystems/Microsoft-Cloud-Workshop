# Introduction
In this workshop, attendees will implement an IoT solution for intelligent vending machines, leveraging facial feature recognition and Azure Machine Learning, to gain a better understanding of building cloud-based machine learning app, and real-time analytics with SQL Database in-memory and columnar indexing. </br></br>
# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed. Also, for multi-day workshops, all virtual machines will be shutdown at 7 PM local time and start at 8AM local time.</br></br>

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
1. **IoT Hub** is provisioned in the resource group, in which you have access.
2. **SQL Database** 
3. **SQL Server** 
5. **Face API (Congnitive Sevices)** 
6. **Azure HDInsight Cluster**   
7. **Virtual Network**
8. **Public IP**
9. **Network Interface**
10. **Load Balancer**
11. **Storage accounts**
> Attendees need not to deploy any Azure resources except a Storage account creating in Exercise 1 > Task 4. All other Azure resources in the workshop are automated and attendees can use those resources during the workshop.
## Notes to Attendees
* While doing **Before hand-on-lab** section, follow the below mentioned steps.
1. You need not to execute **Task 1, Task 2** and **Task 3**. All the resources in these tasks are pre-created (R Server with HDInsight Spark, Lab Virtual Machine and PowerBI Desktop installed on Lab Virtual Machine).
2. In **Task 4**, you need to do **Step 6** to **Step 9**. You can skip all other steps in this task because SSH Client is pre-installed.
3. You can skip **Task 5**.</br></br>
* While doing **Exercise 1 : Environment Setup**, follow the below mentioned steps.
1. In **Task 1**, you will download **Vending Machine Starter Project**.
2. In **Task 2**, **don't deploy IoT Hub**,since it is pre-created. For copying **Connection string - primary key** follow **step 4** to **step 7**.
3. In **Task 3**, **don't deploy Machine Learning Server**,since it is pre-created. Follow **step 10** to **step 15**.
4. You should execute **Task 4** Completely.
5. In **Task 5**, **don't deploy Face API**, since it is pre-created. Execute **Step 3** to **Step 6**.
6. In **Task 6**, **don't deploy SQL Database**,since it is pre-created. Execute **Step 3** and **Step 4** to get the **Database Connection String**
</br></br>
# Known Issues
### Failure while running the following command:
(Exercise 2 > Task 4 > step 23)
> az ml admin node setup --onebox --admin-password Password.1!! --confirm-password Password.1!!

> **Possible Solutions**:

 * I any attendee face any issue while running this command, try following these steps.
   * Run the command : **az ml admin node setup --onebox**
   * Then it will ask for Admin Password : provide the password: **Password.1!!**
   * Confirm the password.

### Not able to see "Take Picture" option:
(Exercise 3 > Task 5 > step 7)
> **Possible Solutions**:

 * Try maximizing and minimizing the window , you can see the part of that "**Take Picture**" option at the bottom of the window.</br></br>

# Notes to Instructors / Proctors
* Attendees need not to deploy any Azure resources except a Storage account creating in Exercise 1 > Task 4. All other Azure resources are automated and attendees can use those resources during the workshop.
* Attendees can refer **Registration Page/Email** for all details of the resources deployed. </br></br>

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.



