# Introduction

This is a supplement guide to  Original lab guide to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

# Verify the pre-provisioned Environment

Here we are providing two versions of environment. One is automated deployment of cloudera cluster and other one is just Azure login, with custom ARM Rbac and policy.

## Automated Deployment of Cloudera Enterprise HUB

1. Here we are managing the deployment of Cloudera Enterprise Hub cluster deploytment. You just not to worry about the cluster deployment. 
1. As soon as you **Launch the lab** from Cloudlabs sign up page. You will get the **Azure and cloudera credentials** within few seconds. 
1. When you loged in to [Azure](https://portal.azure.com) using provided credential, you will see cluster inside resource group **ODL-cdh-46008** (46008 is unique ID for each attendee, will be different for you) with reader permissions on Resource group. 
1. You can login to cloudera manager using master node dns and continue with the lab.

## Azure Subscription access for Clodera Enterprise Hub deployment

1. Here we are just providing you access to azure subscription.
1. As soon as you will sign up and launch the lab you will get azure creadentials. 
1. When you loged in to [Azure](https://portal.azure.com) using provided credential you will see blank resource group **ODL-cdh-46008** (46008 is unique ID for each attendee, will be different for you).
1. You must use existing resource group to deploy Cloudera Enterprise Hub. You will be not able to create new resource group.


## Notes to Attendees
   
# Known Issues

# Notes to Instructors / Proctors


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
