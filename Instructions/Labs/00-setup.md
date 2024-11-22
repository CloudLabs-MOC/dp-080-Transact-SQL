---
lab:
    title: 'Lab Environment Setup - Azure SQL Database'
    module: 'Setup'
---

# Lab Environment Setup

You can complete the Transact-SQL exercises in a sample database in Microsoft Azure SQL Database. Use the instructions in this page to prepare a suitable Azure SQL Database environment.

> **Note**: You will need a [Microsoft Azure subscription](https://azure.microsoft.com/free) in which you have sufficient permissions to create and configure the required resources.

## Exercise 1: Deploy an Azure SQL database

Azure SQL Database is a fully managed platform as a service (PaaS) database engine that handles most database management functions like upgrading, patching, backups, and monitoring without the need for user intervention. Azure SQL Database is always running on the most recent stable version of the SQL Server database engine and a patched operating system, with 99.99% uptime. In this exercise, you are going to deploy an Azure SQL database. 

In this exercise, you will perform the following task:

+ Task 1: Create an Azure SQL database with Adventure Works pre-loaded.

### Estimated Timing: 20 minutes

### Task 1: Create an Azure SQL database with Adventure Works pre-loaded

In this task, you will learn how to use Azure portal to create a single database with Adventure works sample database

#### Steps

1. Login into Azure portal and on the search box type SQL database, then please select the **SQL database** option from the list.

   ![image](../media/Nimage-38.png)

2. Please select the **+ Create** button.

   ![image](../media/Nimage-39.png)


3. Under **Basic** tab, please enter the following details:

    | Settings | Values |
    |  -- | -- |
    | Subscription | *Leave default subscription* |
    | Resource group | Select the resource group name **dp080-<inject key="DeploymentID" enableCopy="false"/>** from the dropdown list** |
    | Database name | **Adventureworks** |
   
    ![image](../media/lab4-1-1.png) 

4. For server, click **Create new**.

    ![image](../media/lab4-1-2.png) 

5. On **Create SQL Database Server** page, please enter the following details and click on **Ok**

    | Settings | Values |
    |  -- | -- |      
    | Server name | **sqlserver<inject key="DeploymentID" enableCopy="false"/>** |
    | Location | **East US** |
    | Authentication method | **Use SQL authentication** |
    | Server admin login | **contosoadmin** |
    | Password |  **Contoso@123** |
    | Confirm password | **Contoso@123** |    
    
    ![image](../media/Nimage-40.png)    

6. After creating the database server, please enter the following and click on **Next : Networking >**

    | Settings | Values |
    |  -- | -- |      
    | Want to use SQL elastic pool? | **No** |    |
    | Compute + storage | Make sure **General Purpose (Standard-series (Gen5), 1 vCores, 32 GB storage, zone redundant disabled)** is selected  |
    | Backup storage redundancy |  **Local redundant storage** |
    
    ![image](../media/Nimage-41.png)
 
7. On the **Networking** tab, modify the below settings as below
   
    | Settings | Values |
    |----------|--------|
    |Connectivity method | Public endpoint |
    |Allow Azure services and resources to access this server | Yes |
    | Add current client IP address | Yes  |
    | Connection policy | Default |
    | Minimum TLS version | TLS 1.2 |


8. Select **Next: Security** at the bottom of the page, modify the below settings as below

   | Settings | Values |
   |----------|--------|
   | Enable Microsoft Defender for SQL | Not now |
   | Ledger | Not configured  |
   | Server identity | Not configured |
   | Server level key | Service-managed key selected |
   | Database level key | Not configured |
   | Enable secure enclaves | Off |

9. Select **Next: Additional settings** at the bottom of the page.

10. On the **Additional settings** tab, in the **Data source** section, select **Sample** for Use existing data and click **Ok** on the **AdventureWorksLT** dialogue box. Instead of an empty blank database, this creates an AdventureWorksLT sample database with tables and data to query and experiment with.

    ![image](../media/Nimage-42.png)

11. After selecting AdventureWorksLT sample database, please select **Review + Create**.

    ![image](../media/Nimage-43.png)

12. After validation is completed successfully, please select **Create**.
 
13. Once the deployment is complete, please select **Go to Resource**.

    ![image](../media/Nimage-44.png)


## Open the query editor

The query editor is a browser-based interface that you can use to run Transact-SQL statements in your database.

1. In the Azure portal, on the page for your **Adventureworks** SQL Database, in the pane on the left, select **Query editor**.
1. On the welcome page, sign into your database using Entra authentication (if necessary, allow access from your client IP address first).
1. In the query editor, expand the **Tables** folder to view the tables in the database.

    > **Note**: If you're familiar with the standard **AdventureWorks** sample database for Microsoft SQL Server, you may notice that we are using a simplified, lightweight (*LT*) version with fewer tables.

1. In the **Query 1** pane, enter the following Transact-SQL code:

    ```sql
    SELECT * FROM SalesLT.Product;
    ```

1. Use the **&#9655; Run** button to run the query, and and after a few seconds, review the results, which includes all columns for all products.
1. Close the Query editor page, discarding your changes if prompted.

Now that you've created the database and learned how to use the query editor to run Transact-SQL code, you can return to the query editor in the Azure Portal at any time to complete the lab exercises.


