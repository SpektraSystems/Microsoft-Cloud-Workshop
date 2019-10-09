# Introduction
This is a supplement guide to ‘Microsoft Cloud Workshop - [Migrate EDW to SQL Data Warehouse](https://github.com/Microsoft/MCW-Migrate-EDW-to-Azure-SQL-Data-Warehouse/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Migrate%20EDW%20to%20Azure%20SQL%20Data%20Warehouse.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com
## Notes

This whiteboard design session will look at the process of migrating an on-premises data warehouse to Azure SQL Data Warehouse. The design session will cover data and schema preparation, data loading, optimizing the data distribution, and building a solution to support ad-hoc queries</br></br>

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.In Azure portal you can navigate to the Resource groups to see the 5 pre-deployed Resource groups.
* You should use the **existing** Resource groups during the lab.
* Navigate to each Resource group and verify that all the pre-deployed resources are in **Resource group-ODL-edw-34502-cohoOnPremEnvir** and other **four** Resource groups are empty. Here 34502 is unique ID of attendee and vary.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.
## Verify Virtual Machine
You are provided a **Free License: SQL Server 2016 SP2 Developer on Windows Server 2016** with additional softwares configured. Administrator credentials of the virtual machine is provided in the lab details page. You can remote into the virutal machine using the provided credentials.


> Note: VM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.
## Verify pre-requisite Azure resources 
1. **Virtual Network**
2. **Public IP**
3. **Network Interface**
4. **Network Security Group** 
## Notes to Attendees
#### While doing [Before the Hands-on-lab](https://github.com/Microsoft/MCW-Migrate-EDW-to-Azure-SQL-Data-Warehouse/blob/master/Hands-on%20lab/Before%20the%20HOL%20-%20Migrate%20EDW%20to%20Azure%20SQL%20Data%20Warehouse.md), follow the below mentioned steps.
1. Do not create **Free License: SQL Server 2016 SP2 Developer on Windows Server 2016** specified in **Task 1**, since it is pre-created.
2. You need to **install** **Azure PowerShell command-line tools** by running the setup file provided on the **Desktop**.
3. You can skip **step 1 to step 6** in **Task 2**, since all specified things are pre-configured.</br>
4. Follow **steps 7 to 9**  **in task 2**, you can find in [Before the HOL lab guide](https://github.com/Microsoft/MCW-Migrate-EDW-to-Azure-SQL-Data-Warehouse/tree/master/Hands-on%20lab).
5. Also you have to perform **Task 3** from **Before the HOL lab guide.** Deploy **cohoOLTP** database in existing **Resource group - ODL-edw-34502-cohoOLTP**, here 34502 is your unique id.
#### While doing [HOL step-by-step Exercise 1](https://github.com/Microsoft/MCW-Migrate-EDW-to-Azure-SQL-Data-Warehouse/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Migrate%20EDW%20to%20Azure%20SQL%20Data%20Warehouse.md), follow the below mentioned steps.
1. While creating **Logical SQL Server** specified in Task 1, you need to select Use Existing under Resource group option and select **Resource group - ODL-edw-34502-cohoDWRG** from the drop down.
2. While creating **Data Factory** specified in Task 2, you need to select Use Existing under Resource group option and select **Resource group - ODL-edw-34502-cohoDataFactory** from the drop down.
3. While creating **SQL Data Warehouse** specified in Task 3, you need to select Use Existing under Resource group option and select **Resource group - ODL-edw-34502-cohoDWRG** from the drop down.
 > Note: Select **Gen1 100-DTU** under Performance level while you create **SQL Data Warehouse.**
4. While creating **Storage Account** specified in Task 4, you need to select Use Existing under Resource group option and select **Resource group - ODL-edw-34502-cohoDWRG** from the drop down.
5. In **Task 5** you can skip the first four steps and you can use the same user details that you are logged in with while creating **Analysis Services**.
6. While creating **Analysis Service** specified in Task 5, you need to select Use Existing under Resource group option and select **Resource group - ODL-edw-34502-cohoDWRG** from the drop down.
7. In **Task 5, step 7**, ensure that your username is populated automatically corresponding to **Administrator** column.</br></br>
# Known Issues
### Issue while installing Power BI Desktop
> **Possible Solutions**:
Go to the link provided in the lab guide. Select **Advanced Download Options**. In the new page you can find a **Download** button. Click on the download button. 
# Notes to Instructors / Proctors

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
