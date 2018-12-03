# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Azure Resource Manager](https://github.com/Microsoft/MCW-Lift-and-shift-Azure-Resource-Manager/blob/master/Hands-on%20Lab/HOL%20step-by-step%20-%20Azure%20Resource%20Manager.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

Azure Resource Manager (ARM) is a one day workshop led by Microsoft or Microsoft partners.These one day focus on hands-on activities that  deploy to infrastructure such as virtual machine, storage, and networking.This lab will also teach the attendees how to deploy virtual machines that are automatically configured by the Azure Automation Desired State Configuration (DSC) service.
* How to author and deploy an ARM template 
* How to perform configuration management with Azure Automation DSC.

 
# Verify the pre-provisioned Environment

1. Launch a browser using incognite or in-private mode, and navigate to https://portal.azure.com. Once prompted, login with the Microsoft Azure credentials you received.   

2. Once you are logged in to the portal, navigate to Resource Groups. 
 
3. Note that you have access to three resource groups – ODL_ARM-xxxxx-01, ODL_ARM-xxxxx-02 and ODL_ARM-xxxxx-03. Note: ODL_ARM-xxxxx-01 has the pre-deployed environment **ODL_ARM-xxxxx-02** and **ODL_ARM-xxxxx-03** is a Resource group with one storage account only. Also you will use **ODL_ARM-xxxxx-02** and **ODL_ARM-xxxxx-03** to deploy new resources. 

4. Navigate to the resource group **ODL_ARM-xxxxx-01** and view the already existing resources such as LABVM Virtual Machine, Disk, etc

5. Using a remote desktop client, open a Remote Desktop Session into the LABVM using the labvmdnsname and credentials you received

6. Now go to -> **C:\Hackathon**, you will see that the student files are already downloaded

7. Now go to Desktop and find the helper-codes folder.  

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a Visual Studio Community 2017 on Windows Server 2016 (x64)Microsoft with additional softwares configured.FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials.

> Note: VM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

* **Helper codes folder** is downloaded on the virtual machine. You should see the icon on **Desktop** or else, you can find / search it from the **Start Menu**

# Known Issues

1. Webpage might takes 25-30 minutes to come up. Refresh the browser after 25-30 mins to view the web page.

2. In the ‘Microsoft Cloud Workshop - [Azure Resource Manager](https://github.com/Microsoft/MCW-Lift-and-shift-Azure-Resource-Manager/blob/master/Hands-on%20Lab/HOL%20step-by-step%20-%20Azure%20Resource%20Manager.md#task-1-parameterize-and-scale-out-the-environment)’ Exercise 5 > Task 1 > Step 1 and 2, some of the code is missing. Users need to make the following changes:

* In Exercise 5 > Task 1 > Step 1, while adding the variables to the end of the variables section you need to add one more variable i.e:
```
    "StorageAccountPrefix": [
      "a",
      "g",
      "m",
      "s",
      "y"
     ]
```
* In Exercise 5 > Task 1 > Step 2, while adding the parameters to the end of the parameters section you need to add one more parameter i.e:
```
    "newStorageAccountSuffix": {
      "type": "string",
      "metadata": {
        "description": "prefix for storage account"
      }
    }
```


# Notes to Instructors / Proctors / Attendees

* Users **should not** use **ODL_ARM-xxxxx-01** for deployment of any resource

* For Exercise 1, 2 and 3, users should use the **ODL_ARM-xxxxx-02** resource group to deploy any resoure or template

* For Exercise 4 and 5, users should use the **ODL_ARM-xxxxx-03** resource group to deploy any resource or template

* For deploying template from Visual Studio, users should use  **stage*********** as the Artifact storage account

* Users should use the same size of vm which is provided in document while deploying templates

* Users should use the Azure Credentials given to them to login to Visual Studio

* While creating Automation Account, user need to select **No** for **Create Azure Run as account**

* User should add the Azure Automation Credential before compiling the DSC files

* **Before deploying any template after Exercise 2 via Visual Studio**, users should execute the three steps given below:

1. In the Solution Explorer, open the **Deploy-AzureResourceGroup.ps1** under the solution. 
 
2. Next, in the Param section, edit the “[string] $StorageContainerName” line; replacing it with this code.    

   **[string] $StorageContainerName = 'stageartifacts',**

3. Save your changes to the Deploy-AzureResourceGroup.ps1 template file and continue with the deploment. 

* Helper codes are given on the desktop to the user incase he face any issue while copying from the document




# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.

  
