# Introduction
This whiteboard design session will look at the process of migrating an on-premises data warehouse to Azure SQL Data Warehouse. The design session will cover data and schema preparation, data loading, optimizing the data distribution, and building a solution to support ad-hoc queries</br></br>
# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed. Also, for multi-day workshops, all virtual machines will be shutdown at 7 PM local time and start at 8AM local time.</br></br>

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.In Azure portal you can navigate to the Resource groups to see the 3 pre-deployed Resource groups.
* You should use the existing Resource groups during the lab.
* Navigate to each Resource group and verify that all the pre-deployed resources are in **Resource group-01** and other two Resource groups are empty.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine
You are provided a **Free License: SQL Server 2016 SP1 Developer on Windows Server 2016** with additional softwares configured. Administrator credentials of the virtual machine is provided in the lab details page. You can remote into the virutal machine using the provided credentials.


> Note: VM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.
## Verify pre-requisite Azure resources 
1. **Virtual Network**
2. **Public IP**
3. **Network Interface**
4. **Network Security Group** 

## Notes to Attendees
#### While doing **Before the Hands-on-lab** section, follow the below mentioned steps.
1. Do not create **Free License: SQL Server 2016 SP1 Developer on Windows Server 2016** specified in **Task 1**, since it is pre-created.
2. You need to **install** **Azure PowerShell command-line tools** by running the setup file provided in the **Desktop**.
3. You can skip **step 1 to step 6** in **Task 2**, since all specified things are pre-configured.</br>
#### While doing **Exercise 1**, follow the below mentioned steps.
1. While creating **Storage account** specified in Task 1, you need to select **Use Existing** under **Resource group** option and select **Resource group - 02** from the drop down.
2. While creating **SQL Data Warehouse** specified in Task 2, you need to select **Use Existing** under **Resource group** option and select **Resource group - 03** from the drop down.
3. In **Task 3** you can skip the first four steps and you can use the same user details that you are logged in with while creating **Analysis Services**.
4. In **step 7**, ensure that your username is populated automatically corresponding to **Administrator** column.</br></br>
# Known Issues
### Issue while installing Power Bi Desktop

> **Possible Solutions**:
Go to the link provided in the lab guide. Select **Advanced Download Options**. In the new page you can find a **Download** button. Click on the download button. 
### RDP Connection Error
> **Possible Solutions**:
If you find a RDP connection error (CredSSP encryption error),go to the below link and follow the steps. 
https://github.com/SpektraSystems/Microsoft-Cloud-Workshop/blob/master/RDP%20CredSSP/README.md
# Notes to Instructors / Proctors

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
