![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Continuous delivery in Azure DevOps
</div>

<div class="MCWHeader2">
Hands-on lab step-by-step
</div>

<div class="MCWHeader3">
August 2019
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2019 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**
<!-- TOC -->

- [Continuous delivery in Azure DevOps hands-on lab step-by-step](#continuous-delivery-in-azure-devops-hands-on-lab-step-by-step)
  - [Abstract and learning objectives](#abstract-and-learning-objectives)
  - [Overview](#overview)
  - [Solution architecture](#solution-architecture)
  - [Requirements](#requirements)
  - [Exercise 1: Create an Azure Resource Manager (ARM) template that can provision the web application, PostgreSQL database, and deployment slots in a single automated process](#exercise-1-create-an-azure-resource-manager-arm-template-that-can-provision-the-web-application-postgresql-database-and-deployment-slots-in-a-single-automated-process)
    - [Task 1: Create an Azure Resource Manager (ARM) template using Azure Cloud Shell](#task-1-create-an-azure-resource-manager-arm-template-using-azure-cloud-shell)
    - [Task 2: Configure the list of release environments parameters](#task-2-configure-the-list-of-release-environments-parameters)
    - [Task 3: Add a deployment slot for the "staging" version of the site](#task-3-add-a-deployment-slot-for-the-%22staging%22-version-of-the-site)
    - [Task 4: Create the dev environment and deploy the template to Azure](#task-4-create-the-dev-environment-and-deploy-the-template-to-azure)
    - [Task 5: Create the test environment and deploy the template to Azure](#task-5-create-the-test-environment-and-deploy-the-template-to-azure)
    - [Task 6: Create the production environment and deploy the template to Azure](#task-6-create-the-production-environment-and-deploy-the-template-to-azure)
  - [Exercise 2: Create Azure DevOps project and Git Repository](#exercise-2-create-azure-devops-project-and-git-repository)
    - [Task 1: Create Azure DevOps Account](#task-1-create-azure-devops-account)
    - [Task 2: Add the Tailspin Toys source code repository to Azure DevOps](#task-2-add-the-tailspin-toys-source-code-repository-to-azure-devops)
  - [Exercise 3: Create Azure DevOps build pipeline](#exercise-3-create-azure-devops-build-pipeline)
    - [Task 1: Create a build pipeline](#task-1-create-a-build-pipeline)
  - [Exercise 4: Create Azure DevOps release pipeline](#exercise-4-create-azure-devops-release-pipeline)
    - [Task 1: Create a release definition](#task-1-create-a-release-definition)
    - [Task 2: Add test and production environments to release pipeline](#task-2-add-test-and-production-environments-to-release-pipeline)
  - [Exercise 5: Trigger a build and release](#exercise-5-trigger-a-build-and-release)
    - [Task 1: Manually queue a new build and follow it through the release pipeline](#task-1-manually-queue-a-new-build-and-follow-it-through-the-release-pipeline)
  - [Exercise 6: Create a feature branch and submit a pull request](#exercise-6-create-a-feature-branch-and-submit-a-pull-request)
    - [Task 1: Create a new branch](#task-1-create-a-new-branch)
    - [Task 2: Make a code change to the feature branch](#task-2-make-a-code-change-to-the-feature-branch)
    - [Task 3: Submit a pull request](#task-3-submit-a-pull-request)
    - [Task 4: Approve and complete a pull request](#task-4-approve-and-complete-a-pull-request)
  - [After the hands-on lab](#after-the-hands-on-lab)
    - [Task 1: Delete resources](#task-1-delete-resources)

<!-- /TOC -->

# Continuous delivery in Azure DevOps hands-on lab step-by-step

## Abstract and learning objectives 

In this hands-on lab, you will learn how to implement a solution with a combination of Azure Resource Manager templates and Azure DevOps to enable continuous delivery with several Azure PaaS services.

At the end of this workshop, you will be better able to implement solutions for continuous delivery with Azure DevOps in Azure, as well create an Azure Resource Manager (ARM) template to provision Azure resources, create an Azure DevOps project with a Git repository, and configure continuous delivery with Azure DevOps.

## Overview

Tailspin Toys has asked you to automate their development process in two specific ways. First, they want you to define an Azure Resource Manager template that can deploy their application into the Microsoft Azure cloud using Platform-as-a-Service technology for their web application and their PostgreSQL database. Second, they want you to implement a continuous delivery process that will connect their source code repository into the cloud, automatically run their code changes through unit tests, and then automatically create new software builds and deploy them onto environment-specific deployment slots so that each branch of code can be tested and accessed independently.

## Solution architecture

![Image that shows the pipeline for checking in code to Azure DevOps that goes through automated build and testing with release management to production.](images/image2.png "Solution architecture")

## Requirements

1.  Microsoft Azure subscription

  >**Note**: This entire lab can be completed using only the Azure Portal.

## Exercise 1: Create an Azure Resource Manager (ARM) template that can provision the web application, PostgreSQL database, and deployment slots in a single automated process

Duration: 60 Minutes

Tailspin Toys has requested three Azure environments (dev, test, production), each consisting of the following resources:

-   App Service

    -   Web App

    -   Deployment slots (for zero-downtime deployments)

-   PostgreSQL Server

    -   PostgreSQL Database

Since this solution is based on Azure Platform-as-a-Service (PaaS) technology, it should take advantage of that platform by utilizing automatic scale for the web app and the PostgreSQL Database PaaS service instead of running virtual machines.

### Task 1: Use Azure Shell as your development environment and download the exercise files

>**Note**: This workshop can be completed using only the Azure Cloud Shell.

1.  From the Azure web portal, launch the **Azure Cloud Shell**. It has common Azure tools preinstalled and configured to use with your account.

    ![This is a screenshot of a icon used to launch the Azure Cloud Shell from the Azure Portal.](images/image3.png "Azure Cloud Shell launch icon")

2.  From inside the Azure Cloud Shell type these commands to configure Git:

    ```
    git config --global user.name "<your name>"
    git config --global user.email <your email>
    ``

3.  Using the Azure Cloud Shell, you can download the file by executing the following command inside the Cloud Shell window (all on one line):

    ```
    curl -o studentfiles.zip https://cloudworkshop.blob.core.windows.net/agile-continous-delivery/studentfiles.zip
    ```

4.  Extract the contents of the file to the new folder. Using the Azure Cloud Shell, you can execute the following command inside the Cloud Shell window:

    ```bash
    unzip studentfiles.zip
    ```

5.  When unzipped, there will be a new folder named **studentfiles**. Navigate to the newly created **studentfiles** directory.

    ```bash
    cd studentfiles
    ```
   
6.  Inside the **studentfiles** folder, there are two folders named **armtemplate** and **tailspintoysweb**. The workshop will refer to these folders throughout the exercises.

>**Note**: Using the Azure Cloud Shell, you can load the integrated code editor at any time with the following command:
```
code .
```

### Task 2: Create an Azure Resource Manager (ARM) template using Azure Cloud Shell

1.  From within the **Azure Cloud Shell** locate the folder where you previously unzipped the Student Files. Open **Code** to this folder with the command below. It should also contain two sub-folders: **armtemplate** and **tailspintoysweb**.

    ```bash
    code .
    ```

    ![In the Code window, the Explorer window is displayed and it shows the student files folder that contains two sub-folders.](images/image22.png "Code Explorer")
  
2.  In the Code Explorer window, select the **armtemplate** sub-folder and open the **azuredeploy.json** file by selecting it.

    ![In the Code Explorer window, azuredeploy.json is highlighted under the armtemplate folder and the file is opened in the Editor window.](images/image23.png "Selecting the azuredeploy.json file")

3.  In the open editor window for the **azuredeploy.json**, scroll through the contents of the Azure Resource Manager Template. This template contains all the necessary code to deploy a Web App and a PostgreSQL database to Azure.

    >**Note**: If you would like to use this template in a future deployment of your own, it can be found in the [Azure Quickstart Templates repository on GitHub](https://github.com/Azure/azure-quickstart-templates). This specific file can be found [here](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-webapp-managed-postgresql/azuredeploy.json).

### Task 3: Configure the list of release environments parameters

1.  Next, you need to configure a list of release environments we'll be deploying to. Our scenario calls for adding three environments: dev, test, and production. This is going to require the addition of some manual code. At the top of the **azuredeploy.json** file, locate the following line of code (on or around line 4).
    ```json
    "parameters": {
    ```  

2.  Insert the following code immediately below that line of code.
    ```json
    "environment": {
        "type": "string",
        "metadata": {
            "description": "Name of environment"
        },
        "allowedValues": [
          "dev",
          "test",
          "production"
        ]
    },
    ```

    After adding the code, it will look like this:

    ![This is a screenshot of the code pasted inside the of the "parameters" object.](images/image24.png "Pasted block of JSON code")

    Save the file.

    >**Note**: The **environment** parameter will be used to generate environment specific names for our web app.

### Task 4: Add a deployment slot for the "staging" version of the site

1.  Next, you need to add the "staging" deployment slot to the web app. This is used during a deployment to stage the new version of the web app. This is going to require the addition of some manual code. In the **azuredeploy.json** file, add the following code to the "resources" array, just above the element for the "connectionstrings" (on or around line 156).

    ```json
    {
        "apiVersion": "2016-08-01",
        "name": "staging",
        "type": "slots",
        "tags": {
            "displayName": "Deployment Slot: staging"
        },
        "location": "[resourceGroup().location]",
        "dependsOn": [
            "[resourceId('Microsoft.Web/Sites/', variables('webAppName'))]"
        ],
        "properties": {
        },
        "resources": []
    },
    ```

    After adding the code, it will look like this:

    Save the file.

    ![This is a screenshot of the code pasted just below the element for the application insights extension in the "resources" array.](images/image39.png "Pasted block of JSON code")

### Task 5: Create the dev environment and deploy the template to Azure

Now that the template file has been uploaded, we'll deploy it several times to create each of our desired environments: "dev", "test", and "production". Let's start with the "dev" environment.

1.  In the **Azure Cloud Shell** terminal, enter the following command and press **Enter**:

    ```bash
    echo "Enter the Resource Group name:" &&
    read resourceGroupName &&
    echo "Enter the location (i.e. westus, centralus, eastus):" &&
    read location &&
    az group create --name $resourceGroupName --location "$location" &&
    az group deployment create --resource-group $resourceGroupName --template-file "$HOME/azuredeploy.json"
    ```
    
    >**Note**: This command is designed to prompt us to enter the resource group name and Azure region (location) we want to deploy our resources to. The script then takes our inputs and passes them as parameters to the Azure CLI command that calls our recently uploaded template file.

    ![In the Azure Cloud Shell window, the command has been entered is we are prompted for the name of the resource group we want to deploy to.](images/image44.png "Azure Cloud Shell window")

2.  Enter the name of a resource group you want to deploy the resources to (i.e. TailspinToysRG). If it does not already exist, the template will create it. Then, press **Enter**.

3.  Next, we're prompted to enter an Azure region (location) where we want to deploy our resources to (i.e. westus, centralus, eastus). Some examples are suggested by our command.
    
    ![In the Azure Cloud Shell window, we are prompted for the location we want to deploy to.](images/image45.png "Azure Cloud Shell window")

4.  Enter the name of an Azure region and then press **Enter**.
   
5.  Next, we're asked to enter a choice for environments we want to deploy to. The template will use our choice to concatenate the name of the environment with the name of the resource during provisioning. 
    
   ![In the Azure Cloud Shell window, we are prompted for the environment we want to deploy to.](images/image46.png "Azure Cloud Shell")

6.  For this first run, select the "dev" environment by entering **1** and then pressing **Enter**. 

7.  Next, we're asked to supply an administrator login (username) for the PostgreSQL server and database. This will be the username credential you would need to enter to connect to your newly created database.

   ![In the Azure Cloud Shell window, we are prompted for the administrative username for the PostgreSQL server and database we want to create.](images/image47.png "Azure Cloud Shell")

8.  Enter a value for the "administratorLogin" and then press **Enter**.

9.  Next, we're asked to supply an administrator password for the PostgreSQL server and database. This will be the password credential you would need to enter to connect to your newly created database.

   ![In the Azure Cloud Shell window, we are prompted for the administrative password for the PostgreSQL server and database we want to create.](images/image48.png "Azure Cloud Shell")

10. Enter a value for the "administratorLoginPassword" and then press **Enter**.

    This will kick off the provisioning process which takes a few minutes to create all the resources for the environment. This is indicated by the "Running" text displayed at the bottom of the Azure Cloud Shell while the command is executing.

   ![The Azure Cloud Shell is executing the template based on the parameters we provided.](images/image49.png "Azure Cloud Shell")

11. After the template has completed, JSON is output to the Azure Cloud Shell window with a "Succeeded" message.

   ![The Azure Cloud Shell has succeeded in executing the template based on the parameters we provided.](images/image50.png "Azure Cloud Shell")

  >**Note**: The above steps were used to provision the "dev" environment. Most of these same steps will be repeated for the "test" and "production" environments below.

### Task 6: Create the test environment and deploy the template to Azure

The following steps are very similar to what was done in the previous task with the exception that you are now creating the "test" environment.

1.  In the Azure Cloud Shell terminal, enter the following command and press **Enter**:

    ```bash
    echo "Enter the Resource Group name:" &&
    read resourceGroupName &&
    echo "Enter the location (i.e. westus, centralus, eastus):" &&
    read location &&
    az group create --name $resourceGroupName --location "$location" &&
    az group deployment create --resource-group $resourceGroupName --template-file "$HOME/azuredeploy.json"
    ```
    
    ![In the Azure Cloud Shell window, the command has been entered is we are prompted for the name of the resource group we want to deploy to.](images/image44.png "Azure Cloud Shell window")

2.  Enter the name of a resource group from earlier that you deployed the resources to (i.e. TailspinToysRG). Then, press **Enter**.
    
    ![In the Azure Cloud Shell window, we are prompted for the location we want to deploy to.](images/image45.png "Azure Cloud Shell window")

3.  Enter the name of the Azure region from earlier and then press **Enter**.
     
   ![In the Azure Cloud Shell window, we are prompted for the environment we want to deploy to.](images/image46.png "Azure Cloud Shell")

4.  For this next run, select the "test" environment by entering **2** and then pressing **Enter**. 

   ![In the Azure Cloud Shell window, we are prompted for the administrative username for the PostgreSQL server and database we want to create.](images/image47.png "Azure Cloud Shell")

5.  Enter the value for the "administratorLogin" and then press **Enter**.

   ![In the Azure Cloud Shell window, we are prompted for the administrative password for the PostgreSQL server and database we want to create.](images/image48.png "Azure Cloud Shell")

6.  Enter a value for the "administratorLoginPassword" and then press **Enter**.

   ![The Azure Cloud Shell is executing the template based on the parameters we provided.](images/image49.png "Azure Cloud Shell")

7.  After the template has completed, JSON is output to the Azure Cloud Shell window with a "Succeeded" message.

   ![The Azure Cloud Shell has succeeded in executing the template based on the parameters we provided.](images/image50.png "Azure Cloud Shell")

### Task 7: Create the production environment and deploy the template to Azure

The following steps are very similar to what was done in the previous task with the exception that you are now creating the "production" environment.

1.  In the Azure Cloud Shell terminal, enter the following command and press **Enter**:

    ```bash
    echo "Enter the Resource Group name:" &&
    read resourceGroupName &&
    echo "Enter the location (i.e. westus, centralus, eastus):" &&
    read location &&
    az group create --name $resourceGroupName --location "$location" &&
    az group deployment create --resource-group $resourceGroupName --template-file "$HOME/azuredeploy.json"
    ```
    
    ![In the Azure Cloud Shell window, the command has been entered is we are prompted for the name of the resource group we want to deploy to.](images/image44.png "Azure Cloud Shell window")

2.  Enter the name of a resource group from earlier that you deployed the resources to (i.e. TailspinToysRG). Then, press **Enter**.
    
    ![In the Azure Cloud Shell window, we are prompted for the location we want to deploy to.](images/image45.png "Azure Cloud Shell window")

3.  Enter the name of the Azure region from earlier and then press **Enter**.
     
   ![In the Azure Cloud Shell window, we are prompted for the environment we want to deploy to.](images/image46.png "Azure Cloud Shell")

4.  For this next run, select the "production" environment by entering **3** and then pressing **Enter**. 

   ![In the Azure Cloud Shell window, we are prompted for the administrative username for the PostgreSQL server and database we want to create.](images/image47.png "Azure Cloud Shell")

5.  Enter the value for the "administratorLogin" and then press **Enter**.

   ![In the Azure Cloud Shell window, we are prompted for the administrative password for the PostgreSQL server and database we want to create.](images/image48.png "Azure Cloud Shell")

6.  Enter a value for the "administratorLoginPassword" and then press **Enter**.

   ![The Azure Cloud Shell is executing the template based on the parameters we provided.](images/image49.png "Azure Cloud Shell")

7.  After the template has completed, JSON is output to the Azure Cloud Shell window with a "Succeeded" message.

   ![The Azure Cloud Shell has succeeded in executing the template based on the parameters we provided.](images/image50.png "Azure Cloud Shell")

8.  In the Azure Portal, navigate to the resource group where all of the resources have been deployed. It should look similar to the screenshot below.

    >**Note**: The specific names of the resources will be slightly different than what you see in the screenshot based on the unique identities assigned.

    ![The Azure Portal is showing all the deployed resources for the resource group we have been using.](images/image51.png "Azure Cloud Shell")

## Exercise 2: Create Azure DevOps project and Git Repository

Duration: 15 Minutes

In this exercise, you will create and configure an Azure DevOps account along with an Agile project.

### Task 1: Create Azure DevOps Account

1.  Browse to the Azure DevOps site at <https://dev.azure.com>.

2.  If you do not already have an account, select the **Start free** button.
    
    ![In this screenshot, a Start free button is shown on the Azure DevOps home page.](images/image56.png "Azure DevOps screenshot")

3.  Authenticate with a Microsoft account.

4.  Choose **Continue** to accept the Terms of Service, Privacy Statement, and Code of Conduct.

5.  Choose a name for new your project. For the purposes of this scenario, we will use "TailspinToys". Choose **Private** in the Visibility section so that our project is only visible to those who we specifically grant access. Then, select **+ Create project**.
    
    ![In the Create a project to get started window, TailspinToys is highlighted in the Project name box, Private is highlighted in the Visibility box, and Create project is highlighted at the bottom.](images/image57.png "Create a project window")

6.  Once the Project is created, click on the **Repos** menu option in the left-hand navigation.

    ![In the TailspinToys project window, Repos is highlighted in the left-hand navigation.](images/image58.png "TailspinToys navigation window")

7.  On the **Repos** page for the **TailspinToys** repository, locate the "or push an existing repository from command line" section. Click the Copy button to copy the contents of the panel. We're going to use these commands in an upcoming step.

    ![In the "Add some code!" window, URLs appear to clone to your computer or push an existing repository from command line.](images/image59.png "TailspinToys is empty. Add some code! window")

### Task 2: Add the Tailspin Toys source code repository to Azure DevOps

In this Task, you will configure the Azure DevOps Git repository. You will configure the remote repository using Git and then push the source code up to Azure DevOps through the command line tools.

1.  Open the **Azure Cloud Shell** to the folder where the Student Files were unzipped (i.e. studentfiles). Then, navigate to the **tailspintoysweb** folder which contains the source code for our web application.

    > **Note**: If this folder doesn't exist ensure you followed the instructions in the Before the HOL.

2. Open Code to this folder by typing: 
   
   ```
   code .
   ``` 

   Then press **Enter**. 
   
   >**Note**: Be sure to include the period after the code command as this is what opens Code to the current folder.
   
3.  In a command prompt window, initialize a local Git repository by running the following command:

    > If a ".git" folder and local repository already exists in the folder, then you will need to delete the ".git" folder first before running the commands below to initialize the Git repository.

    ```
    git init
    ```

4.  Paste the first command you copied from Azure DevOps. It will resemble the command below:
    
    ```
    git remote add origin https://<your-org>@dev.azure.com/<your-org>/TailspinToys/_git/TailspinToys
    ```

5.  Enter the following commands to commit the changes made locally to the new repository:
    
    ```
    git add *
    git commit -m "adding files"
    ```

6.  Push the changes up to the Azure DevOps repository with the following command:

    ```
    git push -u origin --all
    ```

7.  Leave that command prompt window open and switch back to the web browser window for Azure DevOps from the previous Task. Navigate to the Repos > Files page which shows the files in the repository. You may need to refresh the page to see the updated files. Your source code is now appearing in Azure DevOps.

## Exercise 3: Create Azure DevOps build pipeline

Duration: 15 Minutes

Implementing CI and CD pipelines helps to ensure consistent and quality code that's readily available to users. Azure Pipelines is a quick, easy, and safe way to automate building your projects and making them available to users,

In this exercise, you will create a build definition using, Azure Pipelines, that will automatically build the web application with every commit of source code. This will lay the groundwork for us to then create a release pipeline for publishing the code to our Azure environments.
  
### Task 1: Create a build pipeline

Pipelines are made of one or more stages describing a CI/CD process. Stages are the major divisions in a pipeline: "build this app", "run these tests", and "deploy to pre-production" are good examples of stages.

Stages consist of one or more jobs, which are units of work assignable to a particular machine. Both stages and jobs may be arranged into dependency graphs: "run this stages before that one" or "this job depends on the output of that job".

Jobs consist of a linear series of steps. Steps can be tasks, scripts, or references to external templates.

This hierarchy is reflected in the structure of a YAML file.

1.  In your Azure DevOps project, select the Pipelines menu option from the left-hand navigation.

    ![In the Azure DevOps window, Pipelines is highlighted in the ribbon.](images/image68.png "Azure DevOps window")

2.  Select the **New pipeline** button to create a new build pipeline.

    ![In Builds, New pipeline is highlighted.](images/image69.png "Create a new pipeline")

3.  This starts a wizard where you'll first need to select where your current code is located. In a previous step, you pushed code up to Azure Repos. Select the **Azure Repos Git** option.

    ![A screen that shows choosing the Azure Repos option for the TailspinToys project.](images/image70.png "Where is your code?")

4.  Next, you'll need to select the specific repository where your code was pushed. In a previous step, you pushed it to the **TailspinToys** repository. Select the **TailspinToys** git repository.

    ![A screen that shows choosing the TailspinToys repository.](images/image71.png "Select a repository")

5.  Then, you'll need to select the type of pipeline to configure. Although this pipeline contains a mix of technologies, select **ASP.NET Core** from the list of options.

    ![A screen that shows choosing ASP.NET Core pipeline.](images/image72.png "Configure your pipeline")

6.  As a final step in the creation of a build pipeline, you are presented with a configured pipeline in the form of an azure-pipelines.yml file. 
   
7.  This starter YAML file contains a few lines of instructions (shown below) for the pipeline. Let's begin by updating the YAML with more specific instructions to build our application. 

    ![A screen that shows the starter pipeline YAML.](images/image72a.png "Review your pipeline YAML")

The "pool" section specifies which pool to use for a job of the pipeline. It also holds information about the job's strategy for running.

8.  Select and replace the "pool" section with the following code:

    ```yml
    pool:
      name: Hosted VS2017
      demands:
      - msbuild
      - visualstudio
      - vstest
    ```

Steps are a linear sequence of operations that make up a job. Each step runs in its own process on an agent and has access to the pipeline workspace on disk. This means environment variables are not preserved between steps but, file system changes are.

9.  Select and replace the "steps" section with the following code:
    
    ```yml
    steps:
    - task: NuGetToolInstaller@0
      displayName: 'Use NuGet 4.4.1'
      inputs:
        versionSpec: 4.4.1
    ```

Tasks are the building blocks of a pipeline. They describe the actions that are performed in sequence during an execution of the pipeline.

10. Select and replace the entire "task" section with the following code:
    
    >**Note**: The YAML below creates individual tasks for performing all the necessary steps to build and test our application along with publishing the artifacts inside Azure DevOps so they can be retrieved during the upcoming release pipeline process.

    ```yaml
    - task: NuGetCommand@2
      displayName: 'NuGet restore'
      inputs:
        restoreSolution: 'tailspintoysweb.csproj'

    - task: VSBuild@1
      displayName: 'Build solution'
      inputs:
        solution: 'tailspintoysweb.csproj'
        msbuildArgs: '/p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation="$(build.artifactstagingdirectory)\\"'
        platform: 'any cpu'
        configuration: 'release'

    - task: PublishSymbols@2
      displayName: 'Publish symbols path'
      inputs:
        SearchPattern: '**\bin\**\*.pdb'
        PublishSymbols: false
      continueOnError: true

    - task: PublishBuildArtifacts@1
      displayName: 'Publish Artifact'
      inputs:
        PathtoPublish: '$(build.artifactstagingdirectory)'
        ArtifactName: 'TailspinToys-CI'
      condition: succeededOrFailed()
    ```

11. The final result will look like the following:

    ```yml
    pool:
      name: Hosted VS2017
      demands:
      - msbuild
      - visualstudio
      - vstest

    steps:
    - task: NuGetToolInstaller@0
      displayName: 'Use NuGet 4.4.1'
      inputs:
        versionSpec: 4.4.1

    - task: NuGetCommand@2
      displayName: 'NuGet restore'
      inputs:
        restoreSolution: 'tailspintoysweb.csproj'

    - task: VSBuild@1
      displayName: 'Build solution'
      inputs:
        solution: 'tailspintoysweb.csproj'
        msbuildArgs: '/p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation="$(build.artifactstagingdirectory)\\"'
        platform: 'any cpu'
        configuration: 'release'

    - task: PublishSymbols@2
      displayName: 'Publish symbols path'
      inputs:
        SearchPattern: '**\bin\**\*.pdb'
        PublishSymbols: false
      continueOnError: true

    - task: PublishBuildArtifacts@1
      displayName: 'Publish Artifact'
      inputs:
        PathtoPublish: '$(build.artifactstagingdirectory)'
        ArtifactName: 'TailspinToys-CI'
      condition: succeededOrFailed()
    ```

12. Choose the **Save and run** button to save our new pipeline and also kick off the first build.

    ![A screen that shows the contents of azure-pipelines.yml. The Save and run button is highlighted.](images/image73.png "azure-pipelines.yml")    

13. The new azure-pipelines.yml file will automatically be added to the root of your TailspinToys repository. This is done through a git commit that Azure DevOps facilitates. You are then asked to enter a commit description. By default, it will be populated for you. Once again, select the **Save and run** button at the bottom of the screen.

    ![A screen that shows the commit of azure-pipelines.yml. The Save and run button is highlighted.](images/image74.png "Save and run")   

14. The build process will immediately begin and run through the steps defined in the azure-pipelines.yml file. Your Azure DevOps screen will refresh to show you the build process executing, in real-time. 

    ![A screen that shows the real-time output of the build process.](images/image76.png "Real-time output")   

15.  After the build process completes, you should see a green check mark next to each of the build pipeline steps.
  
  ![A screen that shows a successfully completed build pipeline.](images/image77.png "Success") 
    
  Congratulations! You have just created your first build pipeline. In the next exercise, we will create a release pipeline that deploys your successful builds.

## Exercise 4: Create Azure DevOps release pipeline

Duration: 30 Minutes

In this exercise, you will create a release pipeline in Azure DevOps that performs automated deployment of build artifacts to Microsoft Azure. The release pipeline will deploy to three stages: dev, test, and production.

### Task 1: Create a release definition

1.  Select **Releases** on the left-hand navigation. This will bring up the Releases screen. 

    ![A screen that shows the left-side navigation. Releases is highlighted.](images/image84.png "Releases")

2.  Choose the **New pipeline** button to begin the creation of a new release pipeline.

    ![On the Releases screen, the New pipeline button is highlighted.](images/image85.png "Releases screen")

3.  Then, you'll need to select the template that matches the pipeline you are building. Since we are deploying an Azure App Service, select **Azure App Service deployment** from the list of templates and choose the **Apply** button.

    ![A screen that shows choosing Azure App Service deployment.](images/image85a.png "Select a template")

4.  This will present you with the New release pipeline editor which allows you to manage your release stages. A stage is a logical and independent concept that represents where you want to deploy a release generated from a release pipeline. Often times, this is considered an environment. Let's start by giving this stage a name. Change the value "Stage 1" in the editor to "dev" and then select the "X" in the top-right corner to close the panel and save the name change.

    ![A screen that shows Stage details. The Stage name is highlighted. The X is also highlighted.](images/image86.png "Stage")

5.  A release consists of a collection of artifacts in your CD/CD process. An artifact is any deployable component of your application. When authoring a release pipeline, you link the appropriate artifact sources to your release pipeline. In this step, we will connect the artifacts from our previously created build pipeline to this newly created release pipeline. Select the "+ Add" button next to "Artifacts" or the "+ Add an artifact" icon inside the "Artifacts" box. Both buttons perform the same action.

    ![+ Add and + Add an artifact are highlighted in this step.](images/image87.png "New release pipeline")

6.  The Add an artifact panel will display several configurations for linking to an artifact. In the **Source (build pipeline)** dropdown list, select **TailspinToys**. In the **Default version** field, select **Latest**. The panel fields will adjust to show additional details based on your selection. The default values will produce a new release when future builds successfully complete. Select the **Add** button.

    ![On the Add an artifact screen, TailspinToys is highlighted in the Source (build pipeline) field, and the Add button is highlighted at the bottom.](images/image88.png "Add an artifact")

7.  Now, it is time to begin configuring specific tasks to perform our deployment during the dev stage. To navigate to the task editor, select the **Task** menu item.

    ![In the menu, the Tasks item is highlighted.](images/image89.png "New release pipeline")

8.  This brings up the task editor and opens a panel with configuration details for the dev stage we created earlier. The configuration items set here will be made available to the tasks in this stage.

9.  On this panel, we first need to configure the necessary details to connect the task to Azure for deployment. Let's first start by connecting to our Azure subscription. Select the **Advanced options** from the **Authorize** dropdown and configure the **Advanced options** by providing resource group name,subscription and then choose the **Authorize** button to login and authenticate to the selected subscription.
   
   ![On the panel, Azure subscription is highlighted along with the Authorize button.](images/image89b.png "Parameters")

10. Then, in the "App service name field" select the one that begins with **tailspintoys-dev-**.

    ![On the panel, App service name is highlighted.](images/image89c.png "Service connections")

11. Now, let's configure the task specific details. Select the "Deploy Azure App Service" task to bring up the configuration panel for task.

    ![On the screen, Deploy Azure App Service is highlighted.](images/image89d.png "Deploy Azure App Service")

12. In a previous exercise, we created a deployment slot for the web app. Deployment slots are actually live apps with their own hostnames. App content and configuration elements can be swapped between two deployment slots, including the production slot. In the "Azure App Service Deploy" panel, locate the **Deploy to Slot or App Service Environment** checkbox and set it to checked.

    ![On the panel, Deploy to slot is highlighted.](images/image89e.png "Azure App Service Deploy")

13. The checkbox will trigger the panel to update with additional configuration items. In the **Resource group** dropdown, select the appropriate resource group you created in the previous exercise. In the **Slot** dropdown, select **staging**.

    ![On the panel, Resource group and Slot are highlighted.](images/image89f.png "Deployment slot configuration")

14. Now that we've completed the configuration for the "Deploy Azure App Service" task to deploy our application to Azure App Service deployment slot, we'll need a way to swap the staging slot with the production slot. To do that, we'll need to add an additional task to the dev stage. Select the **+** (plus sign) on the task list to create a new task.

    ![On the screen, the plus sign is highlighted.](images/image89g.png "Task list")

15. This opens the "Add tasks" panel. Enter **App Service Manage** into the search box and press **Enter**. Then select the **Azure App Service Manage** task from the search results and select the **Add** button.

    ![On the panel, App Service Manage is entered into the search textbox and Azure App Service Manage is highlighted.](images/image90.png "Add tasks")

16. After adding the new task, we now have two tasks for the dev stage. The new task now needs to be configured. Select the **Swap Slots:** task to open the task configuration panel.

    ![On the screen, the Swap Slots task is highlighted.](images/image91.png "Task list")

17. In the "Azure App Service Manage" task panel there are a few configurations we need to set. First, locate the "Azure subscription" field and select the same subscription used in the "Deploy Azure App Service" task.

18. Locate the "App Service name" field, select the item that begins with **TailspinToysWeb-dev-** just like in the "Deploy Azure App Service" task. In the "Resource Group" field, select **TailspinToys-dev**. In the "Source Slot" field, select **staging**.

    ![On the panel, App Service name, Resource group, and Source Slot are all highlighted.](images/image92.png "Swap Slots task configuration")

19. Let's wrap up this activity by giving our release pipeline a new name. Choose the existing "New release pipeline" name to begin editing it. Change the name to "TailspinToys Release".

    ![On the screen, TailspinToys Release name is highlighted.](images/image92a.png "Release pipeline name change")

20. Select "Save" button at the top of the screen and confirm by clicking the "OK" button.

21. Congratulations! You have just created your first release pipeline.

### Task 2: Add test and production environments to release pipeline

1.  On the Pipeline tab, move your mouse over the dev stage and a select the **Clone** button to create a copy of the tasks from the dev stage. We will use the same steps to deploy to test with a few configuration changes.

    ![On the screen, the Clone button is highlighted.](images/image96.png "Copy the deployment tasks")

2.  Select the newly created stage titled "Copy of dev" to bring up the stage configuration panel.

3.  Change the "Stage name" to **test** and then close the panel.

    ![On the panel, Stage name is highlighted.](images/image96a.png "Stage configuration panel")

4.  Now, we will begin modifying the configuration specifics for the test stage. Select the "1 job, 2 tasks" link for the test stage.

    ![On the screen, 1 job, 2 tasks is highlighted.](images/image97.png "Begin configuring the test stage")

5.  This opens the configuration panel for the stage and includes several pre-populated fields. Locate the **App service name** field and change the value to the app service that starts with **tailspintoys-test-**.

    ![On the panel, App service name is highlighted.](images/image97a.png "Stage configuration panel")

6.  Select the "Deploy Azure App Service" task to bring up the task configuration panel. Notice the settings are the same as when we configured it for the dev stage because we cloned the dev stage to create the test stage. You may need to scroll down the panel to see additional fields.

7.  Locate the **Resource group** field and select the resource group you created earlier. Then, locate the **Slot** field and select **staging**.

    ![On the panel, Resource group and Slot are highlighted.](images/image98.png "Task configuration panel")

8.  Now, select the "Swap Slots" task to bring up the task configuration panel. First, locate the **Display name** field and simplify it to **Swap Slots**. Then, locate the **App Service name** and select the app service that starts with **tailspintoys-test-**. Next, locate the **Resource group** field and change the value to the resource group you created earlier. Finally, locate the **Source Slot** field and set it to **staging**.

    ![On the panel, Display name, App Service name, Resource group, and Source Slot are highlighted.](images/image99.png "Configure the Swap Slots task")

9.  Select the "Save" button at the top of the screen, and confirm by choosing the "OK" button.

10. Congratulations! You have just created a test stage and added it to your pipeline.

11. Repeat all of the steps in Task 2 to create a production stage being careful to enter "production" as a replacement for "test" and selecting "tailspintoys-production" instead of "tailspintoys-test" where applicable. Do not forget to configure to individual steps in the newly cloned production environment.

12. The final release pipeline should look like the screen shot below:

    ![On the screen, all three stages are shown: dev, test, and production.](images/image100.png "The final release pipeline")

13. Now you will enable the continuous deployment trigger, so the release process automatically begins as soon as a build successfully completes. To do this, select the lightning bolt icon in the Artifacts window.

14. This will bring up the Continuous deployment trigger panel. Change the setting to "Enabled".

    ![On the screen, Continuous deployment artifact lightning bolt is highlighted and the Continuous deployment trigger is enabled.](images/image101.png "Enable the continuous deployment trigger")

15. Select Save, and confirm your changes by clicking "OK". Then, close the panel.

Congratulations! You have completed the creation of a release pipeline with three stages.

## Exercise 5: Trigger a build and release

Duration: 10 Minutes

In this exercise, you will trigger an automated build and release of the web application using the build and release pipelines you created in earlier exercises. The release pipeline will deploy to three stages: dev, test, and production.

Any commit of new or modified code to the master branch will automatically trigger a build. The steps below are useful when you want to manually trigger a build without a code change.

### Task 1: Manually queue a new build and follow it through the release pipeline

1.  Select the "Pipelines" menu item from the left-hand navigation. Then, choose the "Queue" button.

    ![On the screen, the Pipelines button and the Queue button are highlighted.](images/image102.png "Queue a new build")

2.  This will present a popup titled "Run pipeline". Select the "Run" button at the bottom of the popup.

    ![On the popup, the Queue button is highlighted.](images/image103.png "Queue button")

3. The screen will refresh and begin to show details about the build process.

4.  If the build is successful, it will resemble the screen shot below.

    ![On the screen, the build has successfully completed. Each task has a green check.](images/image104.png "Successful build results")

5.  Because we configured continuous deployment, the deployment to the dev stage will then be triggered immediately. It will continue through on to the test and production stages. A successful release through all three stages will look like the screen shot below.

    ![On the screen, a successful release through all three stages of deployment.](images/image105.png "A successful release through all three stages")

## Exercise 6: Create a feature branch and submit a pull request

Duration: 20 Minutes

In this exercise, you will create a short-lived feature branch, make a small code change, commit the code, and submit a pull request. You'll then merge the pull request into the master branch which triggers an automated build and release of the application.

In the tasks below, you will make changes directly through the Azure DevOps web interface. These steps could also be performed through an IDE of your choosing or using the Azure Cloud Shell Code Editor.

### Task 1: Create a new branch

1.  Select the "Repos" menu item from the left-hand navigation. Then, choose "Branches".

    ![On the screen, Repos and Branches are highlighted.](images/image106.png "Azure DevOps window")

2.  Select the "New branch" button in the upper right corner of the page.

    ![On the screen, New branch is highlighted.](images/image106a.png "Azure DevOps window")

3.  In the "Create a branch" dialog, enter a name for the new branch. In this scenario, name it "new-heading". In the "Based on" field, be sure **master** is selected.

    ![On the popup window, Name and Based on are highlighted along with the Create branch button.](images/image107.png "Create a branch popup")

4.  Select "Create branch".

### Task 2: Make a code change to the feature branch

1.  Choose the name of the newly created branch. This will present the "Files" window showing all the files in the repository.

    ![On the screen, the new-heading branch is highlighted.](images/image108.png "Branches window")

2.  Next, you'll make a change to a page in the web application inside the web browser.

3.  Select the "ClientApp" folder.

4.  Then choose the "src" folder.

5.  Next select the "app" folder.

6.  Then, the "home" folder.

7.  Locate and select the "home.component.html" file. It will display the contents of the file.

8.  Select the "Edit" button on the top right of the screen to begin editing the page.

    ![On the screen, Edit is highlighted.](images/image109.png "Files window")

9.  Replace the code ```<h1>Welcome to Tailspin Toys v1!</h1>``` on line 1 with the following:

    ```
    <h1>Welcome to Tailspin Toys v2!</h1>
    ```
    
10.  Now that you've completed the code change, select the "Commit..." button on the top right side of the screen.

  ![On the screen, line 6 code change and the Commit button are highlighted.](images/image110.png "Completing the code change")

11. This will present the Commit popup where you can enter a comment. Select the "Commit" button.

    ![On the popup, the Commit button is highlighted.](images/image111.png "Commit dialog popup")

### Task 3: Submit a pull request

1.  Near the top of the screen, locate the "Create a pull request" link.

    ![On the screen, Create a pull request is highlighted.](images/image112.png "Create a pull request")

2.  This brings up the "New Pull Request" page. It shows we are submitting a request to merge code from our **new-heading** branch into the **master** branch. You have the option to change the "Title" and "Description" fields. Locate the "Reviewers" field. Type in **Tailspin** and select the search tooltip. Select the **[TailspinToys]\Tailspin Toys** team from the search results. This assigns The TailspinToys Team (which you are a member of) to review this pull request before it will be merged. The details of the code change are at the bottom of the page.

    ![On the screen, Reviewers is highlighted.](images/image113.png "New Pull Request page")

3.  Select the "Create" button to submit the pull request.

### Task 4: Approve and complete a pull request

Typically, the next few steps would be performed by another team member. This would allow for the code to be peer reviewed. However, in this scenario, you will continue as if you are the only developer on the project.

1.  After submitting the pull request, you are presented with Pull Request review screen. Let's assume all the changes made were acceptable to the review team.

2.  First, select the "Approve" button to approve of the code that was modified submitted as part of the pull request.

3.  This will note that you approved the pull request. Then, choose the "Complete" button to finish and merge the code from the pull request into the master branch.

    ![On the screen, Approve and Complete are highlighted.](images/image114.png "Approve and complete to merge the pull request")

4.  After choosing the Complete button in the previous step, you will be presented with the Complete pull request popup. You can add additional comments for the merge activity. By selecting the "Delete new-heading after merging" option, our branch will be deleted after the merge has been completed. This keeps our repository clean of old and abandoned branches and eliminates the possibility of future confusion.

    ![In the Complete pull request dialog box, Delete new-heading after merging is selected and highlighted, and Complete merge is highlighted at the bottom.](images/image115.png "Complete pull request dialog box")

5.  Select the "Complete merge" button.

6.  You will then see a confirmation of the completed pull request.

    ![On the popup, Complete merge is highlighted.](images/image116.png "Complete pull request popup")

7.  Congratulations! You just created a branch, made a code change, submitted a pull request, approved the pull request, and merged the code.

8.  Because we configured continuous integration and continuous deployment, an automated build will be triggered and deployment to dev stage will then begin immediately after a successful build. It will continue through on to the test and production stages.

    ![On the screen, a new build has been automatically triggered.](images/image117.png "List of builds")

## After the hands-on lab

Duration: 10 Minutes

### Task 1: Delete resources

1.  Now since the hands-on lab is complete, go ahead and delete the resource group you created for the Tailspin Toys deployments along with the Azure DevOps project that were created for this hands-on lab. You will no longer need those resources and it will be beneficial to clean up your Azure Subscription.

These steps should be followed only *after* completing the hands-on lab.
