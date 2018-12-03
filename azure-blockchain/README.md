# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Azure Blockchain](https://github.com/Microsoft/MCW-Azure-Blockchain/blob/master/Hands-on%20lab/HOL%20step-by%20step%20-%20Azure%20Blockchain.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

Azure Blockchain is a one day workshop lead by Microsoft or Microsoft partners.

In this workshop, you will learn how to design a solution with Ethereum Blockchain and several Azure services to collect device telemetry information and enforce contract specifics related to conditions during the transport of goods.

 
# Verify the pre-provisioned Environment

1. Launch a browser using incognite or in-private mode, and navigate to https://portal.azure.com. Once prompted, login with the Microsoft Azure credentials you received.   

2. Once you are logged in to the portal, navigate to Resource Groups. 
 
3. Note that you have access to one resource group – ODL_ARM-xxxxx-01, ODL_ARM-xxxxx-02 and ODL_ARM-xxxxx-03. Note: ODL_ARM-xxxxx-01 has the pre-deployed environment **ODL_ARM-xxxxx-02** and **ODL_ARM-xxxxx-03** is a Resource group with one storage account only. Also you will use **ODL_ARM-xxxxx-02** and **ODL_ARM-xxxxx-03** to deploy new resources. 

4. Navigate to the resource group **ODL_az-blockchain-xxxxx-01** and view the already existing resources such as LABVM Virtual Machine, Disk, etc

5. Using a remote desktop client, open a Remote Desktop Session into the LABVM using the labvmdnsname and credentials you received

6. Now open -> **Visual Studio Code**, you will see that the Solidity Extension is already installed


## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a Visual Studio Community 2017 on Windows Server 2016 (x64)Microsoft with visual studio code configured with Solidity extension.FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials.

> Note: VM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

# Known Issues



# Notes to Instructors / Proctors / Attendees

* Attendees are given Lab VM with Visual Studio Code installed and also Solidity extension pre-installed




# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.

  
