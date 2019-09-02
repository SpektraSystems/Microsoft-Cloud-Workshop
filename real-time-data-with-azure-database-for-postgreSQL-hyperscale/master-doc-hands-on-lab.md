![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
Real-time data with Azure Database for PostgreSQL Hyperscale
</div>

<div class="MCWHeader2">
Hands-on lab step-by-step
</div>

<div class="MCWHeader3">
June 2019
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2019 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Real-time data with Azure Database for PostgreSQL Hyperscale hands-on lab step-by-step](#Real-time-data-with-Azure-Database-for-PostgreSQL-Hyperscale-hands-on-lab-step-by-step)
  - [Abstract and learning objectives](#Abstract-and-learning-objectives)
  - [Overview](#Overview)
  - [Solution architecture](#Solution-architecture)
  - [Requirements](#Requirements)
  - [Before the hands-on lab](#Before-the-hands-on-lab)
  - [Exercise 1: Connect to and set up your database](#Exercise-1-Connect-to-and-set-up-your-database)
    - [Task 1: Connect to the PostgreSQL database](#Task-1-Connect-to-the-PostgreSQL-database)
    - [Task 2: Create a table to store clickstream data](#Task-2-Create-a-table-to-store-clickstream-data)
    - [Task 3: Shard tables across nodes](#Task-3-Shard-tables-across-nodes)
  - [Exercise 2: Add secrets to Key Vault and configure Azure Databricks](#Exercise-2-Add-secrets-to-Key-Vault-and-configure-Azure-Databricks)
    - [Task 1: Obtain and store ADLS Gen2 secrets in Azure Key Vault](#Task-1-Obtain-and-store-ADLS-Gen2-secrets-in-Azure-Key-Vault)
    - [Task 2: Obtain and store Event Hubs (Kafka) secrets in Azure Key Vault](#Task-2-Obtain-and-store-Event-Hubs-Kafka-secrets-in-Azure-Key-Vault)
    - [Task 3: Create a service principal for OAuth access to the ADLS Gen2 filesystem](#Task-3-Create-a-service-principal-for-OAuth-access-to-the-ADLS-Gen2-filesystem)
    - [Task 4: Add the service principal credentials and Tenant Id to Azure Key Vault](#Task-4-Add-the-service-principal-credentials-and-Tenant-Id-to-Azure-Key-Vault)
    - [Task 5: Create an Azure Databricks cluster](#Task-5-Create-an-Azure-Databricks-cluster)
    - [Task 6: Load lab notebooks into Azure Databricks](#Task-6-Load-lab-notebooks-into-Azure-Databricks)
    - [Task 7: Configure Azure Databricks Key Vault-backed secrets](#Task-7-Configure-Azure-Databricks-Key-Vault-backed-secrets)
  - [Exercise 3: Send clickstream data to Kafka and process it in real time](#Exercise-3-Send-clickstream-data-to-Kafka-and-process-it-in-real-time)
    - [Task 1: Configure the KafkaProducer application](#Task-1-Configure-the-KafkaProducer-application)
    - [Task 2: Open notebook and process the streaming data](#Task-2-Open-notebook-and-process-the-streaming-data)
  - [Exercise 4: Rollup real-time data in PostgreSQL](#Exercise-4-Rollup-real-time-data-in-PostgreSQL)
    - [Task 1: Create functions to rollup data](#Task-1-Create-functions-to-rollup-data)
    - [Task 2: Schedule periodic aggregation and execute dashboard queries](#Task-2-Schedule-periodic-aggregation-and-execute-dashboard-queries)
  - [Exercise 5: Create advanced visualizations in Power BI](#Exercise-5-Create-advanced-visualizations-in-Power-BI)
    - [Task 1: Connect to your Postgres data from Power BI](#Task-1-Connect-to-your-Postgres-data-from-Power-BI)
    - [Task 2: Create report](#Task-2-Create-report)
    - [Task 3: Save and publish report](#Task-3-Save-and-publish-report)
  - [After the hands-on lab](#After-the-hands-on-lab)
    - [Task 1: Delete the resource group](#Task-1-Delete-the-resource-group)

<!-- /TOC -->

# Real-time data with Azure Database for PostgreSQL Hyperscale hands-on lab step-by-step

## Abstract and learning objectives

In this hands-on lab, you will implement a proof-of-concept (PoC) for using advanced features of the managed PostgreSQL PaaS service on Azure. These features help make your database more scalable and able to handle the rapid ingest of streaming data while simultaneously generating and serving pre-aggregated data for reports. You will create a resilient stream processing pipeline to ingest, process, and save real-time data to Postgres. Then, you will create complex reports containing advanced visualizations, using a drag-and-drop interface, and use them to build a customizable dashboard that be easily shared with others.

At the end of this hands-on-lab, you will be better able to implement a highly scalable, managed open source database solution that can simultaneously handle real-time data and roll-up and serve data for advanced visualizations.

## Overview

Wide World Importers (WWI) is a traditional brick and mortar business with a long track record of success, generating profits through strong retail store sales of their unique offering of affordable products from around the world. They have a great training program for new employees, that focuses on connecting with their customers and providing great face-to-face customer service. This strong focus on customer relationships has helped set WWI apart from their competitors.

Over time, WWI modernized their business by expanding to online storefronts. During this expansion period, WWI experimented with various marketing tactics to drive online sales, from offering in-store shoppers special discounts online with promotional coupons after making a purchase, to running ad campaigns targeted toward customers based on demographics and shopping habits. These marketing campaigns proved successful, prompting WWI to invest more resources to these efforts and grow their marketing team.

Today, WWI has a host of online stores for various product offerings, from their traditional product catalogs offered by their physical storefronts, to specialized categories like automotive and consumer technology products. This expansion has made it more challenging to analyze user clickstream data, online ad performance, and other marketing campaigns at scale, and to provide insights to the marketing team in real-time.

Real-time marketing analysis is provided through interactive reports and dashboards on WWI's home-grown web platform, ReMarketable. This platform has served them well, but they are currently hindered by their inability to keep up with demand. ReMarketable's primary users are members of the marketing team, and the secondary users are shoppers on their various online platforms for whom website interaction behavior is being tracked. Other sources of data are fed from online ad data generated by ads run on social media platforms and email marketing campaigns. They use this type of data to evaluate ad effectiveness and customer reach, ultimately leading to sales conversions.

Their current challenges with ReMarketable are:

1. **Scale** - WWI is using a PostgreSQL database to store ReMarketable's data. Historical data is growing by over 2.9 GB rows of data per month. It is taking consistently longer to run complex queries. Queries that used to run in 3-5 seconds now take several minutes to complete. This is impacting their users' ability to evaluate up-to-date marketing and website use statistics. Instead of providing real-time reports for all users, they have to keep delaying report runs. They have scaled up their database, but this is becoming very expensive and they will soon hit a ceiling.

2. **Multi-tenancy** - The nature of their marketing and site usage data would benefit from multi-tenancy. Some storefronts generate considerably more data than others and have more marketing analysts that run reports on them than others. WWI believes sharding their database would help take the pressure off lower-volume data stores and also help them scale out. However, this will require re-engineering their database schema and client applications. In addition, sharding will require additional maintenance and increased complexity of aggregated views. These additional challenges and required resources are why they have not pursued this option yet.

3. **Process data while generating roll-ups** - Another byproduct of outgrowing their database is that WWI is having difficulty efficiently processing and ingesting streaming data, while at the same time generating reports for their dashboards. PostgreSQL is well-suited to handle multiple workloads simultaneously when the databases are properly configured, and you are able to appropriately scale up or scale out to multiple nodes. WWI does needs help optimizing their database to handle these demanding workloads at scale. They have looked moving to a non-relational database to speed up queries, but that option added too much complexity to manage multiple databases, losing the ability to wrap their operations inside of transactions, re-architect their application, and migrate their historical data. In addition, they rely on Postgres' ability to create complicated ways of representing and indexing their data, which is impossible to do with a column store. Their need for high transaction volume and a real-time data set ruled out a lot of off-the-shelf data warehouses, where they would need to create a lambda architecture to handle both speeds of feeds.

4. **Resilient stream processing** - WWI is processing their streaming data through a web-based cluster that balances HTTP requests in round-robin fashion. When a node is processing the data and writing it to Postgres, subsequent requests are handled by available nodes. However, if processing fails for any reason, they risk losing that data and have no way to pick up where it left off. They have tried creating their own poison queue to reprocess these failed messages, but if the failed node is unable to add the data to the queue, then it is lost. The WWI technical team is aware of existing products and services that can help improve their stream processing and add resiliency, but they currently lack the skills and bandwidth to implement a solution for these complex scenarios. They are interested to see how Azure can help them rapidly create a solution for resilient stream processing and reduce their technical debt.

5. **Advanced dashboards** - They would like a way to more rapidly create reports and be able to display them on a dashboard that can be customized and show real-time updates.

## Solution architecture

<img src="https://github.com/sumitmalik51/MCW-MCW-Real-time-data-with-Azure-Database-for-PostgreSQL-Hyperscale/blob/master/media/outline-architecture.png">

The solution begins with multiple sources of clickstream data, each from a different tenant, flowing in through a Kafka streaming ingest managed service provided by Azure Event Hubs. This allows Wide World Importers to continue using their existing code to produce Kafka events. An Apache Spark cluster running on Azure Databricks processes and transforms the data in real time, using Structured Streaming. Azure Data Lake Storage is used to store the Structured Streaming checkpoint for resiliency to recover from errors and prevent lost data. Azure Key Vault is used to securely store secrets, such as the Event Hubs and PostgreSQL connection strings, and serves as a backing for Azure Databricks secret scopes. All event data is stored written to an Azure Database for PostgreSQL managed Hyperscale (Citus) database cluster, offering both scale-up and scale-out capability with features that simplify sharding and partitioning time series and multi-tenant data. Data is periodically written to rollup tables, using a background process that runs on a scheduled basis, to provide extremely fast querying of pre-aggregated data that does not interfere with incoming streams of late-arriving data. Websites and Power BI reports and dashboards use this data to provide rich reports that can be run at scale with minimum processing time. An on-premises data gateway cluster runs on several VMs to update the Power BI dashboards at regular intervals to match the pre-aggregation processes that write to the rollup tables.



## Exercise 1: Connect to and set up your database

Duration: 20 minutes

In this exercise, you will obtain your PostgreSQL connection string and use the pgAdmin tool to connect and create your schema for this lab.

### Task 1: Connect to the PostgreSQL database

1. Open the [Azure portal](https://portal.azure.com) and navigate to the resource group you created (`hands-on-lab-SUFFIX` where SUFFIX is your unique identifier).

2. Find your PostgreSQL server group and select it. (The server group name will not have a suffix. Items with names ending in, for example, "-c", "-w0", or "-w1" are not the server group.)

   ![The PostgreSQL server group is highlighted in the resource group.](media/resource-group-pg-server-group.png 'Resource group')

3. Select **Connection strings** in the left-hand menu. Copy the string marked **JDBC**.

   ![The Connection strings item is selected and the JDBC connection string is highlighted.](media/postgres-jdbc-connection-string.png 'Connection strings')

4. Replace "{your_password}" with the administrative password you chose earlier (such as `Abc!1234567890`). The system doesn't store your plaintext password and so can't display it for you in the connection string. **Save the connection string** to Notebook or similar text editor for later.

5. Select **Firewall** in the left-hand menu underneath Security. In the Firewall rules blade, select **+ Add firewall rule for current client IP address (xxx.xxx.xxx.xxx)** to add your IP to the server group's firewall.

   ![The Firewall rules blade is displayed.](media/postgres-firewall.png 'Firewall rules')

6. Launch pgAdmin. Select **Add New Server** on the home page.

   ![The pgAdmin home page is displayed with Add New Server highlighted.](media/pgadmin-home.png 'pgAdmin')

7. In the **General** tab of the Create Server dialog, enter **Lab** into the Name field.

   ![The Name field is filled out in the General tab.](media/pgadmin-create-server-general.png 'Create Server - General tab')

8. Select the **Connection** tab. Enter the following into the fields within the Connection tab:

   - **Host name/address**: paste the host value from the connection string you copied earlier (the string of text between `jdbc:postgresql://` and `:5432`. For example: `<your-server-name>.postgres.database.azure.com`)
   - **Port**: 5432
   - **Maintenance database**: citus
   - **Username**: citus
   - **Password**: The administrative password you chose earlier (such as `Abc!1234567890`).
   - **Save password?**: Check the box.

   ![The previously described fields are filled in within the Connection tab.](media/pgadmin-create-server-connection.png 'Create Server - Connection tab')

9. Click the **Save** button.

10. Expand the newly added **Lab** server under the Servers tree on the pgAdmin home page. You should be able to expand the citus database.

   ![The pgAdmin home page is displayed and the Lab server is expanded.](media/pgadmin-home-connected.png 'pgAdmin home')

### Task 2: Create a table to store clickstream data

In this task, you will create the `events` raw table to capture every clickstream event. This table is partitioned by `event_time` since we are using it to store time series data. The script you execute to create the schema creates a partition every 5 minutes, using [pg_partman](https://www.citusdata.com/blog/2018/01/24/citus-and-pg-partman-creating-a-scalable-time-series-database-on-PostgreSQL/).

Partitioning is the key to high performance, as it allows you to break up data into further smaller chunks based on time windows. One of the keys to fast data loading is to avoid using large indexes. Traditionally, you would use block-range (BRIN) indexes to speed up range scans over roughly-sorted data. However, when you have unsorted data, BRIN indexes tend to perform poorly. Partitioning helps keep indexes small. It does this by dividing tables into partitions, avoiding fragmentation of data while maintaining smaller indexes. In addition, it allows you to query only a smaller portion of the data when you run queries for particular time windows, leading to faster SELECT performance.

1. With the **Lab** server expanded under the Servers tree in pgAdmin, expand Databases then select **citus**. When the citus database is highlighted, select the **Query Tool** button above.

   ![The citus database is selected in pgAdmin, and the Query Tool is highlighted.](media/pgadmin-query-tool-button.png 'Query Tool')

2. Paste the following query into the Query Editor:

   ```sql
   CREATE TABLE events(
       event_id serial,
       event_time timestamptz default now(),
       customer_id bigint,
       event_type text,
       country text,
       browser text,
       device_id bigint,
       session_id bigint
   )
   PARTITION BY RANGE (event_time);

   --Create 5-minutes partitions
   SELECT partman.create_parent('public.events', 'event_time', 'native', '5 minutes');
   UPDATE partman.part_config SET infinite_time_partitions = true;
   ```

3. Press F5 to execute the query, or select the **Execute** button on the toolbar above.

   ![The execute button is highlighted in the Query Editor.](media/pgadmin-query-editor-execute.png 'Query Editor')

4. After executing the query, verify that the new `events` table was created under the **citus** database by expanding **Schemas** -> **public** -> **Tables** in the navigation tree on the left. You may have to refresh the Schemas list by right-clicking, then selecting Refresh.

   ![The new events table is displayed in the navigation tree on the left.](media/pgadmin-events-table.png 'Events table')

### Task 3: Shard tables across nodes

In this task, you will create two rollup tables for storing aggregated data pulled from the raw events table. Later, you will create rollup functions and schedule them to run periodically.

The two tables you will create are:

- **rollup_events_5mins**: stores aggregated data in 5-minute intervals.
- **rollup_events_1hr**: stores aggregated data every 1 hour.

You will notice in the script below, as well as in the script above, that we are sharding each of the tables on `customer_id` column. The sharding logic is handled for you by the Hyperscale server group (enabled by Citus), allowing you to horizontally scale your database across multiple managed Postgres servers. This provides you with multi-tenancy because the data is sharded by the same Tenant ID (customer_id). Because we are sharding on the same ID for our raw events table and rollup tables, our data stored in both types of table are automatically co-located for us by Citus. Furthermore, this means that aggregations can be performed locally without crossing network boundaries when we insert our events data into the rollup tables. Our dashboard queries that execute against the rollup tables are always for a particular tenant (customer id). Hyperscale clusters allow us to parallelize our aggregations across shards, then perform a SELECT on a rollup for a particular customer from the dashboard, and have it automatically routed to the appropriate shard.

Another important thing to note about the rollup tables is that we are using [HyperLogLog](https://en.wikipedia.org/wiki/HyperLogLog) (HLL) data types to very rapidly obtain distinct counts for devices and sessions (`device_distinct_count` and `session_distinct_count`). HyperLogLog is a fixed-size data structure that is extremely fast at estimating distinct value counts with tunable precision. For example, in 1280 bytes `HLL` can estimate the count of tens of billions of distinct values with only a few percent error ([source](https://github.com/citusdata/postgresql-hll)).

It is very common to run `SELECT COUNT(DISTINCT)` on your database to update a dashboard with the number of unique items such as unique purchases of a particular item, unique users, unique page visits, etc. However, when you are using distributed systems, as Wide World Importers is in this situation, calculating unique counts is a difficult problem to solve. One reason for this is that there can be overlapping records across the workers. You could get around this by pulling all the data into a single machine and perform the count, but this does not scale well. Another option is to perform map/reduce functions, which scales, but are very slow to execute. The better option that provides scalability and speed is to use approximation algorithms to provide distinct count results within mathematically provable error bounds. This is why we are using HyperLogLog.

If we were not using HLL, we would be limited to creating a large number of rollup tables. You would need rollup tables for various time periods, and rollup tables to calculate the distinct counts constrained by combinations of columns. For example, if you pre-aggregate over minutes, then you cannot answer queries asking for distinct counts over an hour. If you try and each minute's result to find hourly visits to a specific page, for example, the result will be unreliable because you are likely to have overlapping records within those different minutes. This problem is further complicated when you want to return a count of page visits filtered by time and unique page visit counts by user or a combination of the two. HLL allows us to use one or two rollup tables to answer all of these queries and more. This is because HLL overcomes the overlapping records problem by encoding the data in a way that allows summing up individual unique counts without re-counting overlapping records. When we write data to the HLL columns, we also hash it to ensure uniform distribution. We'll go over this in a bit.

1. With the **Lab** server expanded under the Servers tree in pgAdmin, expand Databases then select **citus**. When the citus database is highlighted, select the **Query Tool** button above.

   ![The citus database is selected in pgAdmin, and the Query Tool is highlighted.](media/pgadmin-query-tool-button.png 'Query Tool')

2. Paste the following query into the Query Editor:

   ```sql
   CREATE TABLE rollup_events_5min (
        customer_id bigint,
        event_type text,
        country text,
        browser text,
        minute timestamptz,
        event_count bigint,
        device_distinct_count hll,
        session_distinct_count hll,
        top_devices_1000 jsonb
    );
    CREATE UNIQUE INDEX rollup_events_5min_unique_idx ON rollup_events_5min(customer_id,event_type,country,browser,minute);
    SELECT create_distributed_table('rollup_events_5min','customer_id');

    CREATE TABLE rollup_events_1hr (
        customer_id bigint,
        event_type text,
        country text,
        browser text,
        hour timestamptz,
        event_count bigint,
        device_distinct_count hll,
        session_distinct_count hll,
        top_devices_1000 jsonb
    );
    CREATE UNIQUE INDEX rollup_events_1hr_unique_idx ON rollup_events_1hr(customer_id,event_type,country,browser,hour);
    SELECT create_distributed_table('rollup_events_1hr','customer_id');

    --shard the events table as well
    SELECT create_distributed_table('events','customer_id');
   ```

   > **Note**: We are sharding each of the tables on the `customer_id` column. This is done by calling the `create_distributed_table` function. When you run this function, Citus inserts metadata marking the table as distributed and creates shards on the worker nodes. Then incoming data into these tables is routed to the right node based on customer id. Because we are sharding on the same ID for our raw events table and rollup tables, our data stored in both types of table are automatically co-located for us by Citus.

3. Press F5 to execute the query, or select the **Execute** button on the toolbar above.

4. After executing the query, verify that the new `rollup_events_1hr` and `rollup_events_5min` tables were created under the **citus** database by expanding **Schemas** -> **public** -> **Tables** in the navigation tree on the left. You may have to refresh the Schemas list by right-clicking, then selecting Refresh.

   ![The new rollup tables are displayed in the navigation tree on the left.](media/pgadmin-rollup-tables.png 'Rollup tables')

## Exercise 2: Add secrets to Key Vault and configure Azure Databricks

Duration: 30 minutes

In this exercise, you will add secrets to Key Vault to securely store secrets, such as your PostgreSQL database, Event Hubs (Kafka), and Azure Data Lake Storage Gen2 credentials. You will then create a new Databricks cluster configure your Azure Databricks workspace to use a Key Vault-backed secret store to access those secrets.

### Task 1: Obtain and store ADLS Gen2 secrets in Azure Key Vault

1. Open the [Azure portal](https://portal.azure.com) and navigate to the resource group you created (`hands-on-lab-SUFFIX` where SUFFIX is your unique identifier).

2. Find your storage account (`wwiadlsSUFFIX`) and select it.

   ![The storage account is highlighted within the resource group.](media/resource-group-storage-account.png 'Storage account')

3. Select **Access keys** under Settings on the left-hand menu. You are going to copy the **Storage account name** and **Key** values and add them as secrets in your Key Vault account.

   ![The storage account Access keys blade is displayed, and the Storage account name and Key are highlighted.](media/storage-account-keys.png 'Access keys')

4. Open a new browser tab or window and navigate to your Azure Key Vault account in the Azure portal, then select **Secrets** under Settings on the left-hand menu. On the Secrets blade, select **+ Generate/Import** on the top toolbar.

   ![In Key Vault, Secrets is selected in the left-hand menu, and the Generate/Import button is highlighted.](media/key-vault-generate-secret.png 'Secrets')

5. On the Create a secret blade, enter the following:

   - **Upload options**: Select Manual.
   - **Name**: Enter "ADLS-Gen2-Account-Name".
   - **Value**: Paste the Storage account name value you copied in an earlier step.

   ![The Create a secret form is displayed with the previously defined field values.](media/key-vault-add-account-name.png 'Create a secret')

6. Select **Create**.

7. Select **+ Generate/Import** again on the top toolbar to create another secret.

8. On the Create a secret blade, enter the following:

   - **Upload options**: Select Manual.
   - **Name**: Enter "ADLS-Gen2-Account-Key".
   - **Value**: Paste the Storage account Key value you copied in an earlier step.

   ![The Create a secret form is displayed with the previously defined field values.](media/key-vault-add-account-key.png 'Create a secret')

9. Select **Create**.

10. Select **+ Generate/Import** again on the top toolbar to create another secret.

11. On the Create a secret blade, enter the following:

    - **Upload options**: Select Manual.
    - **Name**: Enter "Database-Connection-String".
    - **Value**: Paste the PostgreSQL JDBC connection string you copied in an earlier step. Make sure it contains your password.

    ![The Create a secret form is displayed with the previously defined field values.](media/key-vault-add-connection-string.png 'Create a secret')

12. Select **Create**.

### Task 2: Obtain and store Event Hubs (Kafka) secrets in Azure Key Vault

In this task, you will obtain the Event Hubs connection string and store it as a secret in Azure Key Vault, along with the fully qualified domain name. This information will be used by Apache Spark within Azure Databricks to consume and process the streaming data using the Kafka protocol.

1. Open the [Azure portal](https://portal.azure.com) and navigate to the resource group you created (`hands-on-lab-SUFFIX` where SUFFIX is your unique identifier).

2. Find your Event Hubs namespace (`wwi-namespace-SUFFIX`) and select it.

   ![The Event Hubs Namespace is highlighted within the resource group.](media/resource-group-event-hubs.png 'Event Hubs Namespace')

3. Select **Shared access policies** under Settings in the left-hand menu, then select the **RootManageSharedAccessKey** policy.

   ![The Event Hubs shared access policies blade is displayed.](media/event-hubs-shared-access-policies.png 'Shared access policies')

4. Copy the **Connection string-primary key** value and save it to Notepad or similar text editor.

   ![The SAS Policy is displayed and the copy button for the connection string is highlighted.](media/event-hubs-shared-access-policy.png 'SAS Policy')

5. Open a new browser tab or window and navigate to your Azure Key Vault account in the Azure portal, then select **Secrets** under Settings on the left-hand menu. On the Secrets blade, select **+ Generate/Import** on the top toolbar.

   ![In Key Vault, Secrets is selected in the left-hand menu, and the Generate/Import button is highlighted.](media/key-vault-generate-secret.png 'Secrets')

6. On the Create a secret blade, enter the following:

   - **Upload options**: Select Manual.
   - **Name**: Enter "Kafka-Connection-String".
   - **Value**: Paste the Event Hubs connection string you copied in an earlier step.

   ![The Create a secret form is displayed with the previously defined field values.](media/key-vault-add-kafka-connection-string.png 'Create a secret')

7. Select **Create**.

8. Select **+ Generate/Import** again on the top toolbar to create another secret.

9. On the Create a secret blade, enter the following:

   - **Upload options**: Select Manual.
   - **Name**: Enter "Kafka-Server".
   - **Value**: Paste the fully qualified domain name (FQDN) that points to your Event Hubs namespace from the connection string (e.g. `wwi-namespace-SUFFIX.servicebus.windows.net`). The FQDN can be found within your connection string as follows:

   `Endpoint=sb://` **wwi-namespace-SUFFIX.servicebus.windows.net** `/;SharedAccessKeyName=XXXXXX;SharedAccessKey=XXXXXX`

   ![The Create a secret form is displayed with the previously defined field values.](media/key-vault-add-kafka-server.png 'Create a secret')

10. Select **Create**.

### Task 4: Add the service principal credentials and Tenant Id to Azure Key Vault

1. To provide access your ADLS Gen2 account from Azure Databricks you will use secrets stored in your Azure Key Vault account to provide the credentials of your newly created service principal within Databricks. Navigate to your Azure Key Vault account in the Azure portal, then select **Access Policies** and select the **+ Add new** button.

2. Choose the account that you are currently logged into the portal with as the principal and **check Select all** under `key permissions`, `secret permissions`, and `certificate permissions`, then click OK and then click **Save**.

3. Now select **Secrets** under Settings on the left-hand menu. On the Secrets blade, select **+ Generate/Import** on the top toolbar.

   ![Secrets is highlighted on the left-hand menu, and Generate/Import is highlighted on the top toolbar of the Secrets blade.](media/key-vault-generate-secret.png 'Key Vault secrets blade')

4. On the Create a secret blade, enter the following:

   - **Upload options**: Select Manual.
   - **Name**: Enter "WWI-SP-Client-ID".
   - **Value**: Paste the **appId** value from the Azure CLI output you copied in an earlier step.

   ![The Create a secret blade is displayed, with the previously mentioned values entered into the appropriate fields.](media/key-vault-create-wwi-sp-client-id-secret.png 'Create a secret')

5. Select **Create**.

6. Select **+ Generate/Import** again on the top toolbar to create another secret.

7. On the Create a secret blade, enter the following:

   - **Upload options**: Select Manual.
   - **Name**: Enter "WWI-SP-Client-Key".
   - **Value**: Paste the **password** value from the Azure CLI output you copied in an earlier step.

   ![The Create a secret blade is displayed, with the previously mentioned values entered into the appropriate fields.](media/key-vault-create-wwi-sp-client-key-secret.png 'Create a secret')

8. Select **Create**.

9. To perform authentication using the service principal account in Databricks you will also need to provide your Azure AD Tenant ID. Select **+ Generate/Import** again on the top toolbar to create another secret.

10. On the Create a secret blade, enter the following:

    - **Upload options**: Select Manual.
    - **Name**: Enter "Azure-Tenant-ID".
    - **Value**: Paste the **tenant** value from the Azure CLI output you copied in an earlier step.

    ![The Create a secret blade is displayed, with the previously mentioned values entered into the appropriate fields.](media/key-vault-create-azure-tenant-id-secret.png 'Create a secret')

11. Select **Create**.

### Task 5: Create an Azure Databricks cluster

In this task, you will connect to your Azure Databricks workspace and create a cluster to use for this hands-on lab.

1. Return to the [Azure portal](https://portal.azure.com), navigate to the Azure Databricks workspace located in your lab resource group, and select **Launch Workspace** from the overview blade, signing into the workspace with your Azure credentials, if required.

   ![The Launch Workspace button is displayed on the Databricks Workspace Overview blade.](media/databricks-launch-workspace.png 'Launch Workspace')

2. Select **Clusters** from the left-hand navigation menu, and then select **+ Create Cluster**.

   ![The Clusters option in the left-hand menu is selected and highlighted, and the Create Cluster button is highlighted on the clusters page.](media/databricks-clusters.png 'Databricks Clusters')

3. On the Create Cluster screen, enter the following:

   - **Cluster Name**: Enter a name for your cluster, such as lab-cluster.
   - **Cluster Mode**: Select Standard.
   - **Databricks Runtime Version**: Select Runtime: 5.4 (Scala 2.11, Spark 2.4.3).
   - **Python Version**: Select 3.
   - **Enable autoscaling**: Ensure this is checked.
   - **Terminate after XX minutes of inactivity**: Leave this checked, and the number of minutes set to 120.
   - **Worker Type**: Select Standard_DS4_v2.
     - **Min Workers**: Leave set to 2.
     - **Max Workers**: Leave set to 8.
   - **Driver Type**: Set to Same as worker.
   - Expand Advanced Options and enter the following into the Spark Config box:

     ```bash
     spark.driver.extraJavaOptions -Djava.security.properties=
     spark.executor.extraJavaOptions -Djava.security.properties=
     ```

     > **Note**: The two values in the advanced options fixes an issue caused by GCM ciphers being disabled in Databricks version 5.1 and greater. Without these settings, you will receive the following error when attempting to connect to the PostgreSQL Hyperscale cluster: `SSL error: Received fatal alert: handshake_failure`.

   ![The Create Cluster screen is displayed, with the values specified above entered into the appropriate fields.](media/databricks-create-new-cluster.png 'Create a new Databricks cluster')

4. Select **Create Cluster**. It will take 3-5 minutes for the cluster to be created and started.

### Task 6: Load lab notebooks into Azure Databricks

In this task, you will import the notebooks contained in the [Visualizing real-time data with Azure Database for PostgreSQL Hyperscale MCW GitHub repo](https://github.com/Microsoft/MCW-Managed-open-source-databases-on-Azure) into your Azure Databricks workspace.

1. Navigate to your Azure Databricks workspace in the Azure portal, and select **Launch Workspace** from the overview blade, signing into the workspace with your Azure credentials, if required.

   ![The Launch Workspace button is displayed on the Databricks Workspace Overview blade.](media/databricks-launch-workspace.png 'Launch Workspace')

2. Select **Workspace** from the left-hand menu, then select **Users** and select your user account (email address), and then select the down arrow on top of your user workspace and select **Import** from the context menu.

   ![The Workspace menu is highlighted in the Azure Databricks workspace, and Users is selected with the current user's account selected and highlighted. Import is selected in the user's context menu.](media/databricks-workspace-import.png 'Import files into user workspace')

3. Within the Import Notebooks dialog, select **URL** for Import from, and then paste the following into the box: `https://github.com/solliancenet/MCW-Managed-open-source-databases-on-Azure/blob/master/Hands-on%20lab/Resources/OSSDatabases.dbc`

   ![The Import Notebooks dialog is displayed](media/databricks-import-notebooks.png 'Import Notebooks dialog')

4. Select **Import**.

5. You should now see a folder named **OSSDatabases** in your user workspace. This folder contains all of the notebooks you will use throughout this hands-on lab.

### Task 7: Configure Azure Databricks Key Vault-backed secrets

In this task, you will connect to your Azure Databricks workspace and configure Azure Databricks secrets to use your Azure Key Vault account as a backing store.

1. Return to the [Azure portal](https://portal.azure.com), navigate to your newly provisioned Key Vault account and select **Properties** on the left-hand menu.

2. Copy the **DNS Name** and **Resource ID** property values and paste them to Notepad or some other text application that you can reference later. These values will be used in the next section.

   ![Properties is selected on the left-hand menu, and DNS Name and Resource ID are highlighted to show where to copy the values from.](media/key-vault-properties.png 'Key Vault properties')

3. Navigate to the Azure Databricks workspace you provisioned above, and select **Launch Workspace** from the overview blade, signing into the workspace with your Azure credentials, if required.

   ![The Launch Workspace button is displayed on the Databricks Workspace Overview blade.](media/databricks-launch-workspace.png 'Launch Workspace')

4. In your browser's URL bar, append **#secrets/createScope** to your Azure Databricks base URL (for example, <https://westus.azuredatabricks.net#secrets/createScope>).

5. Enter `key-vault-secrets` for the name of the secret scope.

6. Select **Creator** within the Manage Principal drop-down to specify only the creator (which is you) of the secret scope has the MANAGE permission.

   > MANAGE permission allows users to read and write to this secret scope, and, in the case of accounts on the Azure Databricks Premium Plan, to change permissions for the scope.

   > Your account must have the Azure Databricks Premium Plan for you to be able to select Creator. This is the recommended approach: grant MANAGE permission to the Creator when you create the secret scope, and then assign more granular access permissions after you have tested the scope.

7. Enter the **DNS Name** (for example, <https://wwi-keyvault-oss.vault.azure.net/>) and **Resource ID** you copied earlier during the Key Vault creation step, for example: `/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourcegroups/hands-on-lab/providers/Microsoft.KeyVault/vaults/wwi-keyvault-oss`.

   ![Create Secret Scope form](media/create-secret-scope.png 'Create Secret Scope')

8. Select **Create**.

After a moment, you will see a dialog verifying that the secret scope has been created.

## Exercise 3: Send clickstream data to Kafka and process it in real time

Duration: 20 minutes

In this exercise, you will configure and run the `KafkaProducer` application to send clickstream data to your Kafka endpoint provided by your event hub. Then, you will run a notebook with your new Azure Databricks cluster to process the streaming data in real time and write it to your PostgreSQL `events` table.

### Task 1: Configure the KafkaProducer application

1. Navigate to your lab files you extracted for this lab. They should be located in a folder named `MCW-Real-time-data-with-Azure-Database-for-PostgreSQL-Hyperscale` at the root directory of your hard drive (e.g. `C:\MCW-Real-time-data-with-Azure-Database-for-PostgreSQL-Hyperscale`).

2. Navigate to the following folder within: `\Hands-on lab\Resources\Apps`.

3. Open either the `Windows` folder, or the `Linux` folder, depending on your operating system.

   ![The lab files path is highlighted.](media/lab-files.png 'Lab files')

4. Within the folder, open the `appsettings.json` file in a text editor, such as Notepad.

   ![The appsettings.json file is highlighted.](media/lab-files-windows.png 'appsettings.json')

5. Paste your Event Hubs connection string you copied earlier in between the empty quotation marks next to **EVENTHUB_CONNECTIONSTRING**, then **save** the file.

   ![The appsettings.json file is displayed with the Event Hubs connection string value added.](media/app-settings.png 'Opened appsettings.json file')

### Task 2: Open notebook and process the streaming data

In this task, you will open a Databricks notebook and complete the instructions within.

6. Leave the folder open for now and navigate back to your Azure Databricks workspace. You will be instructed to run `KafkaProducer.exe` in this folder after you have completed some steps within the lab notebook.

7. Within your Azure Databricks workspace, select **Workspace** from the left-hand menu, then select **Users** and select your user account (email address). Now select the **OSSDatabases** folder and then select the **1-Consume-Kafka** notebook to open it.

   ![The 1-Consume-Kafka notebook is highlighted in the Databricks workspace.](media/databricks-open-consume-kafka-notebook.png 'Databricks workspace')

8. After opening the notebook, you need to attach your cluster. To do this, select **Detached** in the toolbar, then select your cluster. If your cluster is not running, you will need to start it.

   ![The Detached toolbar item is highlighted, and the lab-cluster is highlighted.](media/databricks-select-cluster.png 'Attach cluster')

9. You can execute each cell by selecting the **play button** on the upper-right portion of the cell, or you can click anywhere in the cell and execute it by entering **Ctrl+Enter** on your keyboard.

   ![The Play button is highlighted in the Databricks cell.](media/databricks-execute-cell.png 'Databricks cell')

10. After you have completed all the steps in the notebook, continue to the next exercise.

## Exercise 4: Rollup real-time data in PostgreSQL

Duration: 15 minutes

In Wide World Importers' pipeline, they are storing event source data (clickstream time series data) in PostgreSQL, within the partitioned `events` table you created earlier. The next step of the pipeline is to aggregate this data into rollup tables so it can be efficiently accessed by their dashboard app or BI tools without impacting performance on the raw data tables.

Rollups are an integral piece of this solution because they provide fast, indexed lookups of aggregates where compute-heavy work is performed periodically in the background. Because these rollups are compact, they can easily be consumed by various clients and kept over longer periods of time.

When you look at the SQL scripts for the `five_minutely_aggregation` and `hourly_aggregation` functions below, you will notice that we are using incremental aggregation to support late, or incoming, data. This is accomplished by using `ON CONFLICT ... DO UPDATE` in the `INSERT` statement.

When executing aggregations, you have the choice between append-only or incremental aggregation. Append-only aggregation (insert) supports all aggregates, including exact distinct and percentiles, but are more difficult to use when handling late data. This is because you have to keep track of which time periods have been aggregated already, since you aggregate events for a particular time period and append them to the rollup table once all the data for that period are available. Incremental aggregation (upsert), on the other hand, easily supports processing late data. The side effect is that it cannot handle all aggregates. We work around this limitation by using highly accurate approximation through HyperLogLog (HLL) and `TopN`. As stated previously, we are aggregating new events and upserting them to our rollup tables. You still need to be able to keep track of which events have already been aggregated. We will do that by tracking the sequence number. There are a few other approaches to do this, and you can read more about why this approach is recommended [here](https://www.citusdata.com/blog/2018/06/14/scalable-incremental-data-aggregation/).

Advanced aggregation is accomplished by using HyperLogLog (HLL) and `TopN`, as discussed earlier. For this topic, reference the `five_minutely_aggregation` and `hourly_aggregation` functions below. Also, please note that where you see the special `excluded` table in the query, it is used to reference values originally proposed for insertion. We are using `hll_has_bigint` to hash the HLL columns `device_id` and `session_id`. This hash function produces a uniformly distributed bit string. HLL does this by dividing values into streams and averaging the results. The `hll_add_agg` and `hll_union` are used to do incremental rollups. `TopN` keeps track of a set of counters in JSONB with the explicit goal of determining the top N (like top 10) items (or our "heavy hitters"). In our case, we're using it to return the top 1000 devices by `device_id`. Similar to HLL, we are using `topn_add_agg` and `topn_union` to do incremental rollups. The `topn_union` function merges `TopN` objects over time periods and dimensions.

### Task 1: Create functions to rollup data

1. Open **pgAdmin** once more. If you no longer have the Query Editor open, expand the **Lab** server under the Servers tree in pgAdmin, expand Databases then select **citus**. When the citus database is highlighted, select the **Query Tool** button above.

   ![The citus database is selected in pgAdmin, and the Query Tool is highlighted.](media/pgadmin-query-tool-button.png 'Query Tool')

2. Within the Query Editor, clear the previous query if needed, paste the following, then **execute the query**.

   ```sql
   CREATE TABLE rollups (
       name text primary key,
       event_table_name text not null,
       event_id_sequence_name text not null,
       last_aggregated_id bigint default 0
   );

   CREATE OR REPLACE FUNCTION incremental_rollup_window(rollup_name text, OUT window_start bigint, OUT window_end bigint)
   RETURNS record
   LANGUAGE plpgsql
   AS $function$
   DECLARE
       table_to_lock regclass;
   BEGIN
       /*
       * Perform aggregation from the last aggregated ID + 1 up to the last committed ID.
       * We do a SELECT .. FOR UPDATE on the row in the rollup table to prevent
       * aggregations from running concurrently.
       */
       SELECT event_table_name, last_aggregated_id+1, pg_sequence_last_value(event_id_sequence_name)
       INTO table_to_lock, window_start, window_end
       FROM rollups
       WHERE name = rollup_name FOR UPDATE;

       IF NOT FOUND THEN
           RAISE 'rollup ''%'' is not in the rollups table', rollup_name;
       END IF;

       IF window_end IS NULL THEN
           /* sequence was never used */
           window_end := 0;
           RETURN;
       END IF;

       /*
       * Play a little trick: We very briefly lock the table for writes in order to
       * wait for all pending writes to finish. That way, we are sure that there are
       * no more uncommitted writes with a identifier lower or equal to window_end.
       * By throwing an exception, we release the lock immediately after obtaining it
       * such that writes can resume.
       */
       BEGIN
           EXECUTE format('LOCK %s IN EXCLUSIVE MODE', table_to_lock);
           RAISE 'release table lock';
       EXCEPTION WHEN OTHERS THEN
       END;

       /*
       * Remember the end of the window to continue from there next time.
       */
       UPDATE rollups SET last_aggregated_id = window_end WHERE name = rollup_name;
   END;
   $function$;

   -- Entries for the rollup tables so that they are getting tracked in incremental rollup process.
   INSERT INTO rollups (name, event_table_name, event_id_sequence_name)
   VALUES ('rollup_events_5min', 'events','events_event_id_seq');

   INSERT INTO rollups (name, event_table_name, event_id_sequence_name)
   VALUES ('rollup_events_1hr', 'events','events_event_id_seq');
   ```

3. Replace the previous query with the following in the Query Editor to create a rollup function that populates the **5-minute rollup table**. Then **execute the query**.

   ```sql
   CREATE OR REPLACE FUNCTION five_minutely_aggregation(OUT start_id bigint, OUT end_id bigint)
   RETURNS record
   LANGUAGE plpgsql
   AS $function$
   BEGIN
       /* determine which page views we can safely aggregate */
       SELECT window_start, window_end INTO start_id, end_id
       FROM incremental_rollup_window('rollup_events_5min');

       /* exit early if there are no new page views to aggregate */
       IF start_id > end_id THEN RETURN; END IF;

       /* aggregate the page views, merge results if the entry already exists */
       INSERT INTO rollup_events_5min
           SELECT customer_id,
                   event_type,
                   country,
                   browser,
                   date_trunc('seconds', (event_time - TIMESTAMP 'epoch') / 300) * 300 + TIMESTAMP 'epoch' AS minute,
                   count(*) as event_count,
                   hll_add_agg(hll_hash_bigint(device_id)) as device_distinct_count,
                   hll_add_agg(hll_hash_bigint(session_id)) as session_distinct_count,
                   topn_add_agg(device_id::text) top_devices_1000
           FROM events WHERE event_id BETWEEN start_id AND end_id
           GROUP BY customer_id,event_type,country,browser,minute
           ON CONFLICT (customer_id,event_type,country,browser,minute)
           DO UPDATE
           SET event_count=rollup_events_5min.event_count+excluded.event_count,
               device_distinct_count = hll_union(rollup_events_5min.device_distinct_count, excluded.device_distinct_count),
               session_distinct_count= hll_union(rollup_events_5min.session_distinct_count, excluded.session_distinct_count),
               top_devices_1000 = topn_union(rollup_events_5min.top_devices_1000, excluded.top_devices_1000);

   END;
   $function$;
   ```

4. Replace the previous query with the following in the Query Editor to create a rollup function that populates the **hourly rollup table**. Then **execute the query**.

   ```sql
   CREATE OR REPLACE FUNCTION hourly_aggregation(OUT start_id bigint, OUT end_id bigint)
   RETURNS record
   LANGUAGE plpgsql
   AS $function$
   BEGIN
       /* determine which page views we can safely aggregate */
       SELECT window_start, window_end INTO start_id, end_id
       FROM incremental_rollup_window('rollup_events_1hr');

       /* exit early if there are no new page views to aggregate */
       IF start_id > end_id THEN RETURN; END IF;

       /* aggregate the page views, merge results if the entry already exists */
       INSERT INTO rollup_events_1hr
          SELECT customer_id,
                  event_type,
                  country,
                  browser,
                  date_trunc('hour', event_time) as hour,
                  count(*) as event_count,
                  hll_add_agg(hll_hash_bigint(device_id)) as device_distinct_count,
                  hll_add_agg(hll_hash_bigint(session_id)) as session_distinct_count,
                  topn_add_agg(device_id::text) top_devices_1000
          FROM events WHERE event_id BETWEEN start_id AND end_id
          GROUP BY customer_id,event_type,country,browser,hour
          ON CONFLICT (customer_id,event_type,country,browser,hour)
          DO UPDATE
          SET event_count = rollup_events_1hr.event_count+excluded.event_count,
              device_distinct_count = hll_union(rollup_events_1hr.device_distinct_count,excluded.device_distinct_count),
              session_distinct_count = hll_union(rollup_events_1hr.session_distinct_count,excluded.session_distinct_count),
              top_devices_1000 = topn_union(rollup_events_1hr.top_devices_1000, excluded.top_devices_1000);
   END;
   $function$;
   ```

### Task 2: Schedule periodic aggregation and execute dashboard queries

In this task, you will use [pg_cron](https://github.com/citusdata/pg_cron) to run the aggregation functions on a periodic basis.

You will then execute queries against the rollup tables that can be used for WWI's dashboard. This is to demonstrate that queries against the pre-aggregated tables that use HLL and TopN advanced aggregation features result in excellent query speeds and flexibility.

1. Replace the previous query with the following in the Query Editor to schedule the rollup functions to execute every 5 minutes, then **execute the query**.

   ```sql
   SELECT cron.schedule('*/5 * * * *', 'SELECT five_minutely_aggregation();');
   SELECT cron.schedule('*/5 * * * *', 'SELECT hourly_aggregation();');
   ```

2. Ensure that the **KafkaProducer** console app is still running and sending data. If not, start it again.

3. **Switch back** to pgAdmin. Although we set the cron schedule to run our query aggregates every five minutes, it is possible that they have not yet run. For now, replace the previous query in the Query Editor with the following to manually run the **5-minute aggregation** query.

   ```sql
   SELECT five_minutely_aggregation();
   ```

4. Replace the previous query with the following in the Query Editor to re-run our **hourly aggregation** function. Then **execute the query**.

   ```sql
   SELECT hourly_aggregation();
   ```

    > The following queries don’t have a `customer_id` in the filter, so these queries will be executed in parallel across all the different nodes in the cluster, leading to fast query performance.

5. Clear the query window and paste the following to retrieve the total number of events and count of distinct devices in the last 15 minutes:

   ```sql
   SELECT sum(event_count) num_events, ceil(hll_cardinality(hll_union_agg(device_distinct_count))) distinct_devices
   FROM rollup_events_5min where minute >=now()-interval '15 minutes' AND minute <=now();
   ```

   > **Note:** If you do not see any values in the result, try adjusting the `15 minutes` interval value to a higher value. If more than fifteen minutes have passed since ingesting the data, you will not see results until you increase this value.

   ![The results output of the first dashboard query is displayed.](media/dashboard-query1.png 'Dashboard query 1')

6. Clear the query window and paste the following to return the count of distinct sessions over the past week:

   ```sql
   SELECT sum(event_count) num_events,
         ceil(hll_cardinality(hll_union_agg(device_distinct_count))) distinct_devices
   FROM rollup_events_1hr
   WHERE hour >=date_trunc('day',now())-interval '7 days'
     AND hour <=now();
   ```

7. Clear the query window and paste the following to return the trend of app usage in the past 2 days, broken down by hour:

   ```sql
   SELECT hour,
         sum(event_count) event_count,
         ceil(hll_cardinality(hll_union_agg(device_distinct_count))) device_count,
         ceil(hll_cardinality(hll_union_agg(session_distinct_count))) session_count
   FROM rollup_events_1hr
   WHERE hour >=date_trunc('day',now())-interval '2 days'
     AND hour <=now()
   GROUP BY hour;
   ```

    > As the next two queries have a filter on `customer_id`, Citus will route the queries to only the node which has the data for that particular customer without needing to touch data for the remaining customers. This leads to faster performance as you need to scan only a small portion of the data.

8. Clear the query window and paste the following to retrieve the total number of events and count of distinct devices in the last 15 minutes by `customer_id`. Remember, the data is sharded by tenant (Customer ID):

   ```sql
   SELECT sum(event_count) num_events, ceil(hll_cardinality(hll_union_agg(device_distinct_count))) distinct_devices
   FROM rollup_events_5min where minute >=now()-interval '15 minutes' AND minute <=now() AND customer_id=1;
   ```

9. Clear the query window and paste the following to return the top devices in the past 30 minutes for customer 2:

   ```sql
   SELECT (topn(topn_union_agg(top_devices_1000), 10)).item device_id
   FROM rollup_events_5min
   WHERE minute >=date_trunc('day',now())-interval '30 minutes'
     AND minute <=now()
     AND customer_id=2;
   ```

## Exercise 5: Create advanced visualizations in Power BI

In this exercise, you will connect to your PostgreSQL database cluster in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) and create advanced visualizations. Then you will export the report to Power BI online so it can be accessed by others and embedded in external websites.

### Task 1: Connect to your Postgres data from Power BI

1. Open Power BI Desktop, then select **Get data**.

   ![Get data is highlighted.](media/pbi-get-data.png 'Power BI Desktop')

2. In the Get Data dialog, search for `postgres` then select the **PostgreSQL database** option. Click **Connect**.

   ![The PostgreSQL database data source is selected.](media/pbi-postgres-data-source-search.png 'Get Data')

3. If you see the following error after clicking **Connect**, you need to [install Npgsql](./Before%20the%20HOL%20-%20Managed%20open%20source%20databases%20on%20Azure.md#Task-7-Install-Npgsql) on your machine, or reboot if you have already completed the installation.

   ![Dialog says this connector requires one or more additional components to be installed before it can be used.](media/pbi-postgresql-error.png 'PostgreSQL database error')

4. In the PostgreSQL database dialog, enter the following into the displayed fields, then click **OK**:

   - **Server**: paste the host value from the connection string you copied earlier (the string of text between `jdbc:postgresql://` and `/citus?`. For example: `<your-server-name>.postgres.database.azure.com:5432`), be sure to include the port at the end (`:5432`).
   - **Database**: enter **citus**.

   ![The Server and Database fields are displayed.](media/pbi-postgresql-server.png 'PostgreSQL database')

5. Enter the following in the form that follows, then click **Connect**:

   - **User name**: Enter **citus**.
   - **Password**: Enter your database password.
   - **Select which level to apply these settings to**: Leave at default value.

   ![The credentials form is displayed.](media/pbi-postgresql-server-creds.png 'PostgreSQL database')

6. In the next screen, a list of tables will appear. Check the box next to **public.events**, then click **Load**.

   ![The public.events table is selected.](media/pbi-navigator.png 'Navigator')

   > Notice that there are several tables whose name starts with `public.events`. This is because of the automatic sharding of the table. The Hyperscale cluster takes care of selecting data from the appropriate shard when you select from the `public.events` table, and handles writing to a shard as well.

### Task 2: Create report

1. In a few moments, you will see a blank report canvas. Select the **Map** visualization from the Visualizations toolbox on the right-hand side.

   ![The Map visualization is highlighted.](media/pbi-map-icon.png 'Visualizations')

2. Drag the **country** field from the `events` table to **Location**, and **event_type** to **Size** within the Map visualization settings.

   ![The fields are shown in their respective locations in the Map settings.](media/pbi-map-settings.png 'Map settings')

3. Your Map visualization should look similar to the following:

   ![The Map visualization is displayed.](media/pbi-map.png 'Map')

4. Click anywhere on the blank canvas to deselect the Map. Select the **Treemap** visualization.

   ![The Treemap visualization is highlighted.](media/pbi-treemap-icon.png 'Visualizations')

5. Drag the **event_id** field from the `events` table to **Values**, and **event_type** to **Group** within the Treemap visualization settings.

   ![The fields are showin in their respective locations in the Treemap settings.](media/pbi-treemap-settings.png 'Treemap settings')

6. Your Treemap visualization should look similar to the following:

   ![The Treemap visualization is displayed.](media/pbi-treemap.png 'Treemap')

7. Click anywhere on the blank canvas to deselect the Map. Select the **Line and clustered column chart** visualization.

   ![The Line and clustered column chart visualization is highlighted.](media/pbi-line-icon.png 'Visualizations')

8. Drag the **country** field from the `events` table to **Column series**, **event_type** to **Shared axis**, and **session_id** to **Column values** within the Line and clustered column chart visualization settings.

   ![The fields are showin in their respective locations in the Line and clustered column chart settings.](media/pbi-line-settings.png 'Visualization settings')

9. Your visualization should look similar to the following:

   ![The visualization is displayed.](media/pbi-line.png 'Line and clustered column chart')

10. Click anywhere on the blank canvas to deselect the Map. Select the **Ribbon chart** visualization.

    ![The Ribbon chart visualization is highlighted.](media/pbi-ribbon-chart.png 'Visualizations')

11. Drag the **browser** field from the `events` table to **Legend**, **country** to **Axis**, and **event_id** to **Value** within the Ribbon chart visualization settings.

    ![The fields are showin in their respective locations in the Ribbon chart settings.](media/pbi-ribbon-settings.png 'Visualization settings')

12. Your Ribbon chart visualization should look similar to the following:

    ![The visualization is displayed.](media/pbi-ribbon.png 'Ribbon chart')

13. When you are done, the report should look like the following. You can click on any item to filter all visualizations. For instance, we selected **download** on the **Treemap** visualization to apply the filter to display only download activities on each chart.

    ![A filtered view of the finished report is displayed.](media/pbi-filtered-report.png 'Power BI filtered report')

### Task 3: Save and publish report

To share your report with others or to enable embedding the report within websites or mobile devices, you can publish it to the online Power BI service.

1. Click the **Publish** button in the ribbon bar above.

   ![The Publish button is highlighted in the ribbon bar.](media/pbi-publish-button.png 'Publish')

2. When prompted to save your changes, click **Save** to save your report to your machine.

   ![A dialog asking whether to save changes is displayed.](media/pbi-save.png 'Save changes')

3. In the Publish dialog, select the **My workspace** destination, then click **Select**.

   ![The My Workspace destination is selected.](media/pbi-publish-destination.png 'Publish to Power BI')

4. In a few moments, you will receive a confirmation that your report was successfully published. Select the link to open your report in Power BI.

   ![The Open in Power BI link is highlighted.](media/pbi-publish-success.png 'Publishing to Power BI')

5. A new browser tab will open, taking you to your published report on the [Power BI website](https://app.powerbi.com). Create a new dashboard by selecting **Pin Live Page** in the toolbar above the report.

   ![The Pin Live Page option is highlighted.](media/pbi-website-report.png 'Power BI website')

6. In the Pin to dashboard dialog, select **New dashboard** and enter a **Dashboard name**, then select **Pin live**.

   ![The pin to dashboard dialog is displayed.](media/pbi-website-pin-live.png 'Pin to dashboard')

You now have the ability to share your report with others, view a mobile version, and edit the published version of your report.

## After the hands-on lab

Duration: 10 mins

In this exercise, you will delete any Azure resources that were created in support of the lab. You should follow all steps provided after attending the Hands-on lab to ensure your account does not continue to be charged for lab resources.

### Task 1: Delete the resource group

1. Using the [Azure portal](https://portal.azure.com), navigate to the Resource group you used throughout this hands-on lab by selecting Resource groups in the left menu.

2. Search for the name of your resource group, and select it from the list.

3. Select Delete in the command bar, and confirm the deletion by re-typing the Resource group name, and selecting Delete.

You should follow all steps provided _after_ attending the Hands-on lab.
