# Introduction

This is a supplement guide to  Original lab guide to be used when you are delivering a hands-on-lab session using Cloud Labs AI platform from Spektra Systems. If you have any questions, please reach out to cloudlabs-support@spektrasystems.com

# Verify the pre-provisioned Environment

Here we are providing two versions of environment. One is automated deployment of cloudera cluster and other one is just Azure login, with custom ARM Rbac and policy.

## Automated Deployment of Cloudera Enterprise HUB

1. Here we are managing the deployment of Cloudera Enterprise Hub cluster deploytment. You just not to worry about the cluster deployment. 
1. As soon as you **Launch the lab** from Cloudlabs sign up page. You will get the **Azure and cloudera credentials** within few seconds. 
1. When you will login to [Azure](https://portal.azure.com) using provided credential you will see cluster inside resource group **ODL-cdh-46008** (46008 is unique ID for each attendee, will be different for you) with reader permissions on Resource group. 
1. You can login to cloudera manager using master node dns and continue with the lab.


## Notes to Attendees

1. You will get four Resource Groups **ODL-TailspinToys-41072-labvm**, **ODL-TailspinToys-41072-dev**, **ODL-TailspinToys-41072-test** and **ODL-TailspinToys-41072-production** already created.
1. Please use **ODL-TailspinToys-41072-dev** instead of **TailspinToys-dev**, **ODL-TailspinToys-41072-test** instead of **TailspinToys-test** and **ODL-TailspinToys-41072-production** instead of **ODL-TailspinToys-41072-production** to deploy TailspinToys project template.
1. When you will login to http://visualstudio.com in [Exercise 2](https://github.com/Microsoft/MCW-Continuous-delivery-in-VSTS-and-Azure/blob/master/Hands-on%20lab/HOL%20step-by-step%20-%20Continuous%20delivery%20in%20VSTS%20and%20Azure.md#exercise-2-create-visual-studio-team-services-team-project-and-git-repository). After creating TailspinToys project you will get different UI, not as shown in lab guide. So you need to turn off all preview features of VSTS.
    - Click on the user profile section in upper right corner and then select Preview features.
      <kbd>![](images/1.jpg "UserProfile")</kbd>
    - Now turn off all the Preview features and continue with your lab.
      <kbd>![](images/2.jpg "Off Preview features")</kbd>
      

# Known Issues

# Notes to Instructors / Proctors


# Help and Support

If you require any help during the workshop, please reach out to the instructor / proctors. Instructors / proctors might escalate the issue to remote support team, at that time, please pass on your AAD User ID (aad_user_xyz), so that it is easier to look up your environment.
