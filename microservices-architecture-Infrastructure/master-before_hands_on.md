# Microservices-architecture-master-doc
![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

## Before the hands-on lab
**Pre-Requisite:**
Once you receive the Lab Environment details after clicking on **Launch Lab**, perform the following task given below before starting with the main lab guide

Synopsis: In this exercise, you will set up your environment for use in the rest of the hands-on lab. You should follow all the steps provided in the Before the hands-on lab section to prepare your environment before attending the hands-on lab.

>**IMPORTANT**: Most Azure resources require unique names. Throughout these steps, you will see the word "SUFFIX" as part of resource names. You should replace this with your Microsoft alias, initials, or other value to ensure the resource is uniquely named.

### Task 1: Provision Service Fabric Cluster

In this task, you will provision the Service Fabric Cluster in Azure.

1.  In the Azure portal, select +Create a Resource, then type "Service Fabric" into the Search the Marketplace box. Select Service Fabric Cluster from the results.

    ![In the Azure Portal, in the left pane, Create a resource is selected. In the Marketplace pane, Everything is selected. In the Everything pane, Service Fabric is typed in the search field, and under Results, Service Fabric Cluster is circled.](media/b4-image5.png "Azure Portal")

2.  On the Service Fabric Cluster blade, select Create.

3.  On the Basics blade of the Create Service Fabric cluster screen, enter the following:

-   Cluster name: Enter **contosoeventssf-SUFFIX**, replacing SUFFIX with your alias, initials, or another value to make the name unique (indicated by a green check in the text box).

-   Operating system: Set to **UbuntuServer 16.04 LTS**

-   Username: Enter **holuser**.

-   Password: Enter **Password.1!!**

-   Subscription: Select the subscription you are using for this lab.

-   Resource Group: Select Create new, and enter **hands-on-lab** for the resource group name. You can add -SUFFIX, if needed to make resource group name unique. This is the resource group you will use for all resources you create for this hands-on lab.

-   Location: Select the region to use. Select the closest region to your current location.

-   Select OK.

    ![On the Basics blade, all fields are set to the previously defined settings.](media/b4-image6.png "Basics blade")

4.  On the Cluster configuration blade, set the following:

-   Node type count: **Select 1**.

-   Node type 1 (Primary): **Select to configure required settings**. On the Node type configuration blade enter:

    -   Node type name: Enter **Web**.

    -   Durability tier: Leave **Bronze** selected.

    -   Virtual machine size: Select a VM size of **D1\_V2 Standard** and select Select on the Choose a size blade.

        ![On the Cluster configuration blade, under Virtual Machine Size, D1\_V2 Standard is indicated.](media/ClusterConfigurationBlade.png "Cluster configuration blade")
       

    -   Single node cluster: Leave unchecked.

    -   Initial VM scale set capacity: Leave set to **5**.

    -   Custom endpoints: Enter **8082, 8083**. This will allow the microservices to be accessible through the cluster.

    -   Configure advanced settings: Leave unchecked.

    -   Select OK on the Node type configuration blade.

    -   Select OK on the Cluster configuration blade.

    ![The Create Service Fabric cluster blade, Cluster configuration blade, and Node type configuration blade all display with the previously defined settings.](media/b4-image8.png "Three blades")

5.  On the Security blade, you can provide security settings for your cluster. This configuration is completed up front, cannot be changed later. Set the following:

-   Configuration Type: Leave "Basic" selected.

-   Key vault: Select to configure required settings. On the Key vault configuration blade select "Create a new vault".

-   On the "Create key vault" configuration blade enter:

    -   Name: **hands-on-lab-SUFFIX**

    -   Resource Group: Select "Create new" and set the name as **hands-on-lab**
    
    -   Location: Use the same location as the first resource group you created.

        ![Create a new vault in selected in the Key vault blade, and the values specified above are entered into the Create key vault blade.](media/b4-image9.png "Key vault and Create key vault blades")

-   Select "Create" on the Create key vault configuration blade. Wait for the key vault deployment to complete.

-   When the key vault deployment completes you will return to the Security configuration blade. You will see a warning that the key vault is not enabled for deployment. Follow these steps to resolve the warning:

    -   Choose "Edit access policies for hands-on-lab-SUFFIX".

    -   In the Access policies configuration blade, choose the link "Click to show advanced access policies".

    -   Check the "Enable access to Azure Virtual Machines for deployment" checkbox.

    -   Choose "Save". When the key vault update completes, close the Access policies blade.

        ![Basic Configuration Type is selected on the Security blade, and Edit access policies for hands-on-lab-SUFFIX is selected. Enable access to Azure Virutal Machines for deployment is checked in the Access policies blade on the right.](media/b4-image10.png "Security and Access policies blades")

    -   Enter **hands-on-lab-SUFFIX** as the certificate name. Then choose OK on the Security configuration blade.

6.  On the Summary blade, review the summary, and select Create to begin provisioning the new cluster.

    ![The Summary blade displays with the message that Validation has passed.](media/b4-image11.png "Summary blade")

7.  It can take up to 30 minutes or more to provision your Service Fabric Cluster. You can move on to the next task while you wait.

>**Note**: If you experience errors related to lack of available cores, you may have to delete some other compute resources, or request additional cores to be added to your subscription, and then try this again.


### Task 5: Install Docker for Windows

In this task, you will install Docker for Windows on your Lab VM.

1.  On your Lab VM, open a browser and navigate to: <https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe>.

2.  If prompted, select Save File to download the installer on the Lab VM.

    ![In the Opening Docker for Windows Installer.exe dialog box, a message asks if you want to save the file. At the bottom, the Save File button is circled.](media/b4-dockerwin.png "Opening Docker for Windows Installer.exe dialog box")

3.  When finished, open the folder where the file was downloaded.

4.  Double-click the Docker for Windows Installer.exe file in order to run the installer.
    
    ![In the Installing Docker Desktop window, a message indicates that the Docker required files are being downloaded.](media/b4-dockerwin-install.png "Installing Docker Desktop window")

5.  Follow the instructions to install the application.

6.  Once the Docker for Windows installation completes, select the Close and log out button.  This action will log out the current session.

7.  Reconnect to the LabVM virtual machine by repeating the step 5 in Task 3.

8.  When prompted, select Ok on the Docker Desktop dialog box that asks you if you want to enable Hyper-V and Containers features.  This action will restart the virtual machine.

    ![In the Docker Desktop dialog box, a message asks you if you want to enable Hyper-V and Containers features.  The Ok button is circled](media/b4-dockerwin-hyperv.png "Docker Desktop dialog box")
    
9. Reconnect to the LabVM virtual machine by repeating the step 5 in Task 3.

10. Wait for Docker for Windows to start.  You can see its status on the icon in the tray bar.  When Docker starts successfully, it will display the Welcome window.

    ![The Welcome window indicates that Docker was started successfully.](media/b4-dockerwin-started.png "Docker Welcome window")



### Task 6: Install Service Fabric SDK for Visual Studio

In this task, you will install the latest Service Fabric SDK for Visual Studio on your Lab VM.

1.  On your Lab VM, open a browser, and navigate to: <https://docs.microsoft.com/azure/service-fabric/service-fabric-get-started>.

2.  Scroll down on the page to the Install the SDK and tools section and select **Install the Microsoft Azure Service Fabric SDK** under the To use Visual Studio 2017 heading.  Regardless of the heading, it can be installed on Visual Studio 2019.

    ![In the Install the SDK and tools section, the link to Install the Microsoft Azure Service Fabric SDK is circled.](media/b4-image30.png "Install the SDK and tools section")

3.  Run the downloaded executable and select Install in the Web Platform Installer screen.
   
    ![The Web Platform Installer window displays the information for Microsoft Azure Service Fabric SDK - 3.1.283.](media/install-service-fabric-sdk.png "Web Platform Installer window")


4.  On the Prerequisites screen, select I Accept.

    ![The Web Platform Installer Prerequisites window lists the file name and file size to be downloaded. At the bottom, the I Accept button to download additional software and review the license is circled.](media/b4-image32.png "Web Platform Installer Prerequisites window")

5.  Select Finish when the install completes.

    ![The Web Platform Installer Finish window shows that the installation was successful, and lists the products that were installed.](media/b4-image33.png "Web Platform Installer Finish window")

6.  Select Exit on the Web Platform installer to close it.

7.  Restart the VM to complete the installation and start the local Service Fabric cluster service.

### Task 7: Setup Service Fabric certificate

When you create a new Service Fabric Cluster using the portal, a secure cluster is deployed. In order to later on be able to make use of it, a certificate setup is required.

In this task, you will download the required certificate and install it on your Lab VM.

1.  In the Azure portal, navigate to the Resource Group you created previously and where you created the Key vault that supports the cluster.

2.  Select the key vault from the list of resources in the resource group.

    ![In the Azure Portal Resource Group pane, in the list of resources, the hands-on-lab-SUFFIX key vault is circled.](media/b4-image34.png "Resource group list")

3.  Under the Settings category in the menu, select Certificates and then select the existing certificate.

    ![In the Settings section, Certificates and the existing certificate are circled.](media/b4-image35.png "Certificates")

4.  Select the Current Version of the existing certificate.

    ![In the certificate list, the existing certificate is circled.](media/b4-image36.png "Existing certificate")

5.  In the certificate information blade, select Download in PFX/PEM format and save the certificate.

    ![In the certificate information blade, download the private certificate.](media/b4-image37.png "Download certificate")

6.  Copy the downloaded certificate into the Lab VM.

7.  On the Lab VM, double-click the copied certificate to initiate its installation. Select Local Machine as the Store Location and select Next.

    ![Double-click the certificate to install, select Local Machine and select Next.](media/b4-image38.png "Certificate Import Wizard")

8.  Select Next.

    ![Select Next.](media/b4-image39.png "File to import")

9.  Select Next.

    ![Select Next.](media/b4-image40.png "Private key protection")

10. Select Next.

    ![In the Certificate Store, select Next.](media/b4-image41.png "Certificate Store")

11. Select Finish.

    ![In the review panel, select next.](media/b4-image42.png "Review panel")

12. When the import finishes successfully, select OK.

    ![Import success.](media/b4-image43.png "Import successful")

13. On the Lab VM, double-click the copied certificate once again to initiate its installation. Select Current User as the Store Location and select Next.

    ![Double-click the certificate to install, select Local Machine and select Next.](media/b4-image44.png "Certificate Import Wizard")

14. Select Next.

    ![Select Next.](media/b4-image39.png "File to import")

15. Select Next.

    ![Select Next.](media/b4-image40.png "Private key protection")

16. Select Next.

    ![In the Certificate Store, select Next.](media/b4-image41.png "Certificate Store")

17. Select Finish.

    ![In the review panel, select next.](media/b4-image42.png "Review panel")

18. When the import finishes successfully, select OK.

    ![Import success.](media/b4-image43.png "Import successful")


You should follow all steps provided *before* performing the Hands-on lab.

