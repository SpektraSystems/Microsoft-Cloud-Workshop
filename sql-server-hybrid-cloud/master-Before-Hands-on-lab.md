![Microsoft Cloud Workshop](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshop")

<div class="MCWHeader1">
SQL Server hybrid cloud
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
June 2019
</div>


Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2019 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.


# SQL Server hybrid cloud before the hands-on lab setup guide 

## Before the hands-on lab

Duration: 60 minutes

In this exercise, you deploy an on-premises environment and the Azure infrastructure necessary to support the disaster recovery site in Azure. The on-premises environment will be hosted in an Azure Resource Group.

### Task 1: Deploy the on-premises environment

1. Browse to the Azure portal at <https://portal.azure.com> and verify that you are logged in with the subscription that you wish to use for this lab.

    >**Note**: You may need to launch an \"in-private\" session in your browser if you have multiple Microsoft Accounts.
    
    
    
    
2. Click the **Deploy to Azure** button below.

    <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fopsgility%2Fcw-sql-hybrid-cloud%2Fmaster%2Fazure-deploy.json" rel="nofollow">
    <img src="https://camo.githubusercontent.com/9285dd3998997a0835869065bb15e5d500475034/687474703a2f2f617a7572656465706c6f792e6e65742f6465706c6f79627574746f6e2e706e67" data-canonical-src="http://azuredeploy.net/deploybutton.png" style="max-width:100%;"></a>





3. Make sure to Add Resource Groups **SUFFIX** in the Second Resource Group Section. 

  <img
src="https://github.com/sumitmalik51/MCW-SQL-Server-hybrid-cloud-/blob/master/images/before-the-hands-on-lab/Screenshot%20(46).png">







4. On the **Custom deployment** blade, select **Cloud Shop1-SUFFIX ** under the **Resource group**. Choose the region pair of your CloudShop2-SUFFIX resource group location. In our lab document we have chosen the **East US 2/Central US** region pair. Accept the terms and conditions and click **Purchase**.

   <img src="https://github.com/sumitmalik51/MCWsqlhybridcloud-/blob/master/images/before-the-hands-on-lab/Screenshot%20(48).png">

   

5. Wait for the deployment to complete. This may take up to 60 minutes.


## Summary

In this exercise, you deployed and validated your "On-Premises" environment and your Azure disaster recovery site. You also verified that all three servers have successfully joined the domain. In the lab you will reconfigure your on-premises environment for high availability.

You should follow all steps provided *before* attending the Hands-on lab.
