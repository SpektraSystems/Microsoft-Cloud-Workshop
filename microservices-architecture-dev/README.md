# Introduction

Microservices and serverless architectures is one day workshp lead by Microsoft and Microsoft partners.These day focus on hands-on activities and helping an online concert ticket vendor survive the first 5 minutes of crushing load. It will handle the client's scaling needs through microservices built on top of Service Fabric, and apply smooth updates or roll back failing updates.Attendees will design an implementation of load testing to optimize the architecture for handling spikes in traffic.

Attendees will learn how to:
•	Implement scale and resiliency with Service Fabric
•	Enable serverless solutions with Azure Functions
•	Control API access with API Management
•	Provide query flexibility with Cosmos DB

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **10 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed. Also, for multi-day workshops, all virtual machines will be shutdown at 7 PM local time and start at 8AM local time.

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

### Powershell option is not available in the Queue Trigger box
(Exercise 3 > Task 5 > Step 29)
> **Possible Solutions**:

 * Before going to Step 29, attendees should perform the following step.
   * In the top-right corner of the **Choose a Template** page, **Enable** the **Experimental Language Support**.
   
 ### Debug the contosoEvents.web
 (Exercise 6 > TASK 2)
 > **Possible Solutions**:
 
 * After debugging it will shows exception error, user need to update homecontroller.cs file in line no.18 & 19.
      //if (events.Any())
       if (events != null)

# Notes to Instructors / Proctors

* For installing Service Fabric SDK, setup file is already provided in the desktop inside a folder. User can click on the setup file to install Service Fabric SDK.

# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.



