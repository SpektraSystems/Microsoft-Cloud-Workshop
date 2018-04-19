# Introduction

In the Enterprise Ready Cloud workshop, attendees will learn how to use Azure RBAC and Policy to help control usage within an Azure subscription, or across subscriptions using Management Groups. They will also learn how to use DevTest Labs, including setting up VPN access to the test environment.

# Sign-up for Workshop Environment

To make it easier for you to work on the labs, you are provided with pre-provisioned Azure environment. You will receive sign-up link for the lab environment from your instructor. 

* Register for the lab environment by providing your information and clicking on **Submit** button.

* On the next page, click the **Launch Lab** button.
 
* Wait for the lab environment to be provisioned. Sometimes this can take upto **30 minutes**. Once environment provisioning is complete, you will receive details in email as well as in the browser.
 
 > Note: Lab environment is enabled only for specific duration or workshop end time - whichever is earlier. At the end of the allowed time, environment will be self-destructed. Also, for multi-day workshops, all virtual machines will be shutdown at 7 PM local time and start at 8AM local time.


# Verify the pre-provisioned Environment

No Azure resources are pre-provisioned for this lab. Only the Azure subscription is required.

Open a browser instance in private or incognito mode and login to [Microsoft Azure Portal](https://portal.azure.com) using the credentials provided.

> Note: You might have an existing Azure Credential. For the pre-provisioned environment, new Microsoft Azure environment is provisioned and new AAD user is created for you. To prevent conflict with your existing accounts, it is advised to use In Private mode of IE / Edge or Incognito mode of Chrome browser.


# Known Issues

* This lab uses Management Groups. This is a preview feature, and therefore has certain limitations. One of these limitations is that Management Groups currently don't work with CSP subscriptions (the Azure Portal does not allow you to assign subscriptions to Management Groups). Since the Spektra lab environment is based on a CSP subscription, the lab steps involving Management Groups will not work.  **To workaround, students should skip any steps relating to Management Groups and apply Azure Policy at the subscription scope instead.**

# Notes to Instructors / Proctors

* Be aware of the Known Issues above.


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.



