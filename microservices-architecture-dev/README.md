# Introduction

This is a supplement guide to ‘Microsoft Cloud Workshop - [Microservices Architecture Dev](https://github.com/Microsoft/MCW-Microservices-architecture/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Microservices%20architecture%20-%20Developer%20edition.md)’, to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

Microservices and serverless architectures is one day workshp lead by Microsoft and Microsoft partners.These day focus on hands-on activities and helping an online concert ticket vendor survive the first 5 minutes of crushing load. It will handle the client's scaling needs through microservices built on top of Service Fabric, and apply smooth updates or roll back failing updates.Attendees will design an implementation of load testing to optimize the architecture for handling spikes in traffic.

Attendees will learn how to:
•	Implement scale and resiliency with Service Fabric
•	Enable serverless solutions with Azure Functions
•	Control API access with API Management
•	Provide query flexibility with Cosmos DB

# Verify the pre-provisioned Environment

## Verify Azure Access

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / IE Edge or Incognito mode of Chrome browser.

## Verify Virtual Machine

You are provided a **Visual Studio 2017 Community edition** with additional softwares configured. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: VM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.

## Verify other Azure resources
* **Service Fabric Cluster** is provisioned in the resource group, in which you have access.  
* Other Azure resources such as **Virtual Network, Public IP, Network Interface, Load Balancer, Storage accounts and Virtual Machine Scale Set** as required by the Service Fabric Cluster and VM.

# Known Issues

### Download Starter Project
(Exercise 1 > Task 1 > Step 1)
>  **Possible Solutions**:

* On your Lab VM, download the starter project from here: https://github.com/Microsoft/MCW-Microservices-architecture/blob/master/Hands-on%20lab/ContosoEventsPoC-Dev-June2018Update.zip?raw=true 

### Powershell option is not available in the Queue Trigger box
(Exercise 3 > Task 5 > Step 29)
> **Possible Solutions**:

 * Before going to Step 29, attendees should perform the following step.
   * In the top-right corner of the **Choose a Template** page, **Enable** the **Experimental Language Support**.
   
### ContosoEventsapp Unavailable
(Exercise 3 > Task 1 > Step 10)
> **Possible Solutions**:
 
 * Users should change the Project version for contosoeventsapp **2.1** to **1.4**. 
   
   
 ### Debug the contosoEvents.web
 (Exercise 6 > TASK 2)
 > **Possible Solutions**:
 
 * After debugging it will shows exception error, user need to update homecontroller.cs file in line no.18 & 19.
      //if (events.Any())
       if (events != null)

### Connecting DSVM with RDP having issue addresses CredSSP

> **Possible Solutions**:

* With the release of the March 2018 Security bulletin, there was a fix that addressed a CredSSP, “Remote Code Execution” vulnerability (CVE-2018-0886) which could impact RDP connections. 
**Resolution**
Please follow the instruction under https://github.com/SpektraSystems/Microsoft-Cloud-Workshop/blob/master/RDP%20CredSSP/README.md

# Notes to Instructors / Proctors

* For installing Service Fabric SDK, setup file is already provided in the desktop inside a folder. User can click on the setup file to install Service Fabric SDK.

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.



