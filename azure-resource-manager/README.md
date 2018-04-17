# Introduction

Azure Resource Manager (ARM) is a one day workshop lead by Microsoft or Microsoft partners.These one day focus on hands-on activities that  deploy to infrastructure such as virtual machine, storage, and networking.This lab will also teach the attendees how to deploy virtual machines that are automatically configured by the Azure Automation Desired State Configuration (DSC) service.
* How to author and deploy an ARM template 
* How to perform configuration management with Azure Automation DSC.
 
# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
  
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed.
 
# Verify the pre-provisioned Environment

1. Launch a browser using incognite or in-private mode, and navigate to https://portal.azure.com. Once prompted, login with the Microsoft Azure credentials you received.   

2. Once you are logged in to the portal, navigate to Resource Groups. 
 
3. Note that you have access to three resource groups – ODL_ARM-xxxxx-01, ODL_ARM-xxxxx-02 and ODL_ARM-xxxxx-03. Note: ODL_ARM-xxxxx-01 has the pre-deployed environment **ODL_ARM-xxxxx-02** and **ODL_ARM-xxxxx-03** is a Resource group with one storage account only. Also you will use **ODL_ARM-xxxxx-02** and **ODL_ARM-xxxxx-03** to deploy new resources. 

4. Navigate to the resource group **ODL_ARM-xxxxx-01** and view the already existing resources such as LABVM Virtual Machine, Disk, etc

5. Using a remote desktop client, open a Remote Desktop Session into the LABVM using the labvmdnsname and credentials you received

6. Now go to -> **C:\Hackathon**, you will see four files

7. Now go to Desktop and find the helper-codes folder.  

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a Visual Studio Community 2017 on Windows Server 2016 (x64)Microsoft with additional softwares configured.FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials.

> Note: VM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

* **Helper codes folder** and **Hands-on Lab Guide** is downloaded on the virtual machine. You should see the icon on **Desktop** or else, you can find / search it from the **Start Menu**

# Known Issues

Webpage might takes 25-30 minutes to come up. Refresh the browser after 25-30 mins to view the web page.

# Notes to Instructors / Proctors

1. Before deploying any template via Visual Studio,  In the Solution Explorer, open the **Deploy-AzureResourceGroup.ps1** under the solution. 
 
2. Next, in the Param section, edit the “[string] $StorageContainerName” line; replacing it with this code.    

   **[string] $StorageContainerName = 'stageartifacts',**

3. Save your changes to the Deploy-AzureResourceGroup.ps1 template file and continue with the deploment. 

* For Exercise 1, 2 and 3, users should use the **ODL_ARM-xxxxx-02** resource group to deploy any resoure or template
* For Exercise 4 and 5, users should use the **ODL_ARM-xxxxx-03** resource group to deploy any resource or template
* For deploying template from Visual Studio, users should use  **stage*********** as the Artifact storage account 
* Users should use the same size of vm which is provided in document.
* Users should use the Azure Credentials given to them to login to Visual Studio

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.

  
