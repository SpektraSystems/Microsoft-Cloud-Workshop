# Introduction
This session is designed to help attendees gain a better understanding of implementing architectures leveraging aspects from microservices and serverless architectures, by helping an online concert ticket vendor survive the first 5 minutes of crushing load. They will handle the client's scaling needs through microservices built on top of Service Fabric, and apply smooth updates or roll back failing updates. Finally, students will design an implementation of load testing to optimize the architecture for handling spikes in traffic. </br></br>
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
You are provided a **Visual Studio 2017 Community edition** with additional softwares configured. FQDN of the virtual machine and administrator credentials are provided in the lab details page. You can remote into the virutal machine using the provided credentials and validate the following:

> Note: VM is provisioned in the resource group, in which you have access. Once you login to Microsoft Azure Portal, you can navigate to this VM to find more details.
## Verify pre-requisite Azure resources
1. **Service Fabric Cluster** is provisioned in the resource group, in which you have access.  
2. **Virtual Machine Scale Set** 
3. **Virtual Network**
4. **Public IP**
5. **Network Interface**
6. **Load Balancer**
7. **Storage accounts** 

## Notes to Attendees
While doing **Before the Hands-on-lab** section, follow the below mentioned steps.
1. Do not create **Service Fabric Cluster** specified in **Task 1**, since it is pre-created.
2. Do not create **Lab Virtual Machine** specified in **Task 2**, since it is pre-created.
3. You can skip **Task 3**, since Internet Explorer Enhanced Security Configuration is already off  
4. Don’t install **Google Chrome browser** specified in **Task 4**, since it’s pre-installed in Lab VM
5. In **Task 5**, you need not to download **Microsoft Azure Service Fabric SDK**. You can install it by opening the **Service Fabric SDK** setup file provided inside a folder in the **Desktop**
6. In **Task 6**, you will **Validate Service Fabric ports**</br></br>

# Known Issues
### Powershell option is not available in the Queue Trigger box
(Exercise 2 > Task 5 > Step 29)
> **Possible Solutions**:

 * Before going to Step 29, attendees should perform the following step.
   * In the top-right corner of the **Choose a Template** page, **Enable** the **Experimental Language Support**. </br></br>

# Notes to Instructors / Proctors
* For installing Service Fabric SDK, setup file is already provided in the desktop inside a folder. User can click on the setup file to install Service Fabric SDK.</br></br>
# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
