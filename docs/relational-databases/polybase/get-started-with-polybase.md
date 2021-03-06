---
title: PolyBase の概要 | Microsoft Docs
ms.custom: ''
ms.date: 08/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: database
ms.reviewer: ''
ms.suite: sql
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: get-started-article
helpviewer_keywords:
- PolyBase
- PolyBase, getting started
- Hadoop import
- Hadoop export
- Azure blob storage import
- Azure blob storage export
- Hadoop import, PolyBase getting started
- Hadoop export, Polybase getting started
caps.latest.revision: 78
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: cfde818a22771ba7bfa08259e3a34eff68fb1aea
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="get-started-with-polybase"></a>PolyBase の概要
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このトピックでは、SQL Server インスタンスでの PolyBase の実行に関する基本事項について説明します。
  
 次の手順を実行すると、次の結果が得られます。  
  
-   PolyBase がインストールされ、サーバー上で実行可能になる  
  
-   PolyBase オブジェクトを作成するステートメントの例を確認できる  
  
-   SQL Server Management Studio (SSMS) で PolyBase オブジェクトを管理する方法を理解できる  
  
-   PolyBase オブジェクトを使用するクエリの例を確認できる    

## <a name="install-polybase"></a>PolyBase のインストール  
PolyBase をインストールしていない場合は、「[PolyBase のインストール](../../relational-databases/polybase/polybase-installation.md)」をご覧ください。 インストールに関する記事では、前提条件について説明します。
  
### <a name="how-to-confirm-installation"></a>インストールの確認方法  
 インストールが完了したら、次のコマンドを実行して、PolyBase が正常にインストールされていることを確認します。 PolyBase がインストールされている場合は 1 を返し、それ以外の場合は 0 を返します。  
  
```sql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  
  
##  <a name="supported"></a> PolyBase を構成する  
 インストールの後、Hadoop バージョンまたは Azure Blob Storage のどちらかを使うように SQL Server を構成する必要があります。 PolyBase は、Hortonworks Data Platform (HDP) と Cloudera Distributed Hadoop (CDH) の 2 つの Hadoop プロバイダーをサポートしています。  サポートされている外部データ ソースは次のとおりです。  
  
-   Linux/Windows Server 上の Hortonworks HDP 1.3  
  
-   Linux 上の Hortonworks HDP 2.1 ～ 2.6

-   Windows Server 上の Hortonworks HDP 2.1 - 2.3  
  
-   Linux 上の Cloudera CDH 4.3  
  
-   Linux 上の Cloudera CDH 5.1 – 5.5、5.9 - 5.13  
  
-   Azure BLOB ストレージ  
 
Hadoop は、その新しいリリースの "Major.Minor.Version" パターンに従います。 サポートされているメジャー リリースおよびマイナー リリース内のすべてのバージョンがサポートされています。
 

>  [!NOTE]
> Azure Data Lake Store 接続は、Azure SQL Data Warehouse でのみサポートされています。
  
### <a name="external-data-source-configuration"></a>外部データ ソースの構成  
  
1.  [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) ‘hadoop connectivity’ を実行し、適切な値を設定します。 既定で、hadoop connectivity は 7 に設定されています。 値を見つけるには、「[PolyBase Connectivity Configuration &#40;Transact-SQL&#41; (PolyBase 接続性構成 &#40;Transact-SQL&#41;)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。  
      ```sql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  **services.msc**を使用して SQL Server を再起動する必要があります。 SQL Server を再起動すると、次のサービスが再起動します。  
  
    -   SQL Server PolyBase Data Movement Service  
  
    -   SQL Server PolyBase エンジン  
  
 ![services.msc での PolyBase サービスの停止と開始](../../relational-databases/polybase/media/polybase-stop-start.png "services.msc での PolyBase サービスの停止と開始")  
  
### <a name="pushdown-configuration"></a>プッシュダウンの構成  
 クエリ パフォーマンスを高めるには、Hadoop クラスターへのプッシュダウン計算を有効にします。  
  
1.  SQL Server のインストール パスで **yarn-site.xml** というファイルを検索します。 通常、このパスは次のとおりです。  
  
    ```  
  
    C:Program FilesMicrosoft SQL ServerMSSQL13.MSSQLSERVERMSSQLBinnPolybaseHadoopconf  
  
    ```  
  
2.  Hadoop コンピューターで、Hadoop 構成ディレクトリ内の対応するファイルを検索します。 このファイル内の構成キー yarn.application.classpath の値をコピーします。  
  
3.  SQL Server コンピューターで、 **yarn.site.xml ファイル** 内の **yarn.application.classpath** プロパティを検索します。 Hadoop コンピューターからこの値要素に値を貼り付けます。  
  
4. すべての CDH 5.X バージョンで、yarn.site.xml file の最後か mapred-site.xml file に mapreduce.application.classpath 構成パラメーターを追加する必要があります。 HortonWorks では、yarn.application.classpath 構成内にこれらの構成が含まれます。 例については、「[PolyBase の構成](../../relational-databases/polybase/polybase-configuration.md)」を参照してください。

 
## <a name="scale-out-polybase"></a>PolyBase をスケール アウトする  
 PolyBase グループ機能では、外部データ ソースからの大量のデータ セットを、クエリ パフォーマンスの向上のためにスケールアウト形式で処理するために、SQL Server インスタンスのクラスターを作成することができます。  
  
1.  複数台のマシンに、PolyBase を使用する SQL Server をインストールします。  
  
2.  1 つの SQL Server をヘッド ノードとして選択します。  
  
3.  [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md)を実行して、他のインスタンスをコンピューティング ノードとして追加します。  
  
    ```  
    -- Enter head node details:   
    -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';  
  
    ```  
  
4.  コンピューティング ノードで PolyBase Data Movement Service を再起動します。  
  
 詳細については、「 [PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)」を参照してください。  
  
## <a name="create-t-sql-objects"></a>T-SQL オブジェクトの作成  
 Hadoop または Azure Storage のいずれかの外部データ ソースに依存するオブジェクトを作成します。  
  
### <a name="hadoop"></a>Hadoop  
  
```sql  
-- 1: Create a database scoped credential.  
-- Create a master key on the database. This is required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- 2: Create a database scoped credential  for Kerberos-secured Hadoop clusters.  
-- IDENTITY: the Kerberos user name.  
-- SECRET: the Kerberos password  
  
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1   
WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
  
-- 3:  Create an external data source.  
-- LOCATION (Required) : Hadoop Name Node IP address and port.  
-- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
-- CREDENTIAL (Optional):  the database scoped credential, created above.  
  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
        TYPE = HADOOP,   
        LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',   
        RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',   
        CREDENTIAL = HadoopUser1        
);  
  
-- 4: Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).    
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
-- 5:  Create an external table pointing to data stored in Hadoop.  
-- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
  
CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
        [SensorKey] int NOT NULL,   
        [CustomerKey] int NOT NULL,   
        [GeographyKey] int NULL,   
        [Speed] float NOT NULL,   
        [YearMeasured] int NOT NULL  
)  
WITH (LOCATION='/Demo/',   
        DATA_SOURCE = MyHadoopCluster,  
        FILE_FORMAT = TextFileFormat  
);  
  
-- 6:  Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
### <a name="azure-blob-storage"></a>Azure BLOB ストレージ  
  
```sql  
--1: Create a master key on the database.  
-- Required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- Create a database scoped credential  for Azure blob storage.  
-- IDENTITY: any string (this is not used for authentication to Azure storage).  
-- SECRET: your Azure storage account key.  
  
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential   
WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';  
  
--2:  Create an external data source.  
-- LOCATION:  Azure account storage account name and blob container name.  
-- CREDENTIAL: The database scoped credential created above.  
  
CREATE EXTERNAL DATA SOURCE AzureStorage with (  
        TYPE = HADOOP,   
        LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
        CREDENTIAL = AzureStorageCredential  
);  
  
--3:  Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat
WITH (  
       FORMAT_TYPE = DELIMITEDTEXT,   
       FORMAT_OPTIONS (
         FIELD_TERMINATOR ='|',   
         USE_TYPE_DEFAULT = TRUE
       )
);
         
  
--4: Create an external table.  
-- The external table points to data stored in Azure storage.  
-- LOCATION: path to a file or directory that contains the data (relative to the blob container).  
-- To point to all files under the blob container, use LOCATION='/'   
  
CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
        [SensorKey] int NOT NULL,   
        [CustomerKey] int NOT NULL,   
        [GeographyKey] int NULL,   
        [Speed] float NOT NULL,   
        [YearMeasured] int NOT NULL  
)  
WITH (LOCATION='/Demo/',   
        DATA_SOURCE = AzureStorage,  
        FILE_FORMAT = TextFileFormat  
);  
  
--5: Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
## <a name="polybase-queries"></a>PolyBase クエリ  
 PolyBase が適している機能には、次の 3 つがあります。  
  
-   外部テーブルに対するアドホック クエリ  
  
-   データのインポート。  
  
-   データのエクスポート。  
  
### <a name="query-examples"></a>クエリの例  
  
-   アドホック クエリ  
  
    ```sql  
    -- PolyBase Scenario 1: Ad-Hoc Query joining relational with Hadoop data   
    -- Select customers who drive faster than 35 mph: joining structured customer data stored   
    -- in SQL Server with car sensor data stored in Hadoop.  
    SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,   
            Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
    FROM Insured_Customers, CarSensor_Data  
    WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35   
    ORDER BY CarSensor_Data.Speed DESC  
    OPTION (FORCE EXTERNALPUSHDOWN);    -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
    ```  
  
-   インポート、データ  
  
    ```sql  
    -- PolyBase Scenario 2: Import external data into SQL Server.  
    -- Import data for fast drivers into SQL Server to do more in-depth analysis and  
    -- leverage Columnstore technology.  
  
    SELECT DISTINCT   
            Insured_Customers.FirstName, Insured_Customers.LastName,   
            Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
    INTO Fast_Customers from Insured_Customers INNER JOIN   
    (  
            SELECT * FROM CarSensor_Data where Speed > 35   
    ) AS SensorD  
    ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
    ORDER BY YearlyIncome  
  
    CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
    ```  
  
-   データのエクスポート  
  
    ```  
    -- PolyBase Scenario 3: Export data from SQL Server to Hadoop.  
  
    -- Enable INSERT into external table  
    sp_configure ‘allow polybase export’, 1;  
    reconfigure  
  
    -- Create an external table.   
    CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
            [FirstName] char(25) NOT NULL,   
            [LastName] char(25) NOT NULL,   
            [YearlyIncome] float NULL,   
            [MaritalStatus] char(1) NOT NULL  
    )  
    WITH (  
            LOCATION='/old_data/2009/customerdata',  
            DATA_SOURCE = HadoopHDP2,  
            FILE_FORMAT = TextFileFormat,  
            REJECT_TYPE = VALUE,  
            REJECT_VALUE = 0  
    );  
  
    -- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
    INSERT INTO dbo.FastCustomer2009  
    SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
    ON (T1.CustomerKey = T2.CustomerKey)  
    WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
    ```  
  
## <a name="managing-polybase-objects-in-ssms"></a>SSMS での PolyBase オブジェクトの管理  
 SSMS では、外部テーブルが別のフォルダー **[外部テーブル]** に表示されます。 外部データ ソースおよび外部ファイル形式は、 **[外部リソース]** の下のサブフォルダーにあります。  
  
 ![SSMS の PolyBase オブジェクト](../../relational-databases/polybase/media/polybase-management.png "SSMS の PolyBase オブジェクト")  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 DMV を使用して、パフォーマンスおよびクエリをトラブルシューティングします。 詳細については、「 [PolyBase のトラブルシューティング](../../relational-databases/polybase/polybase-troubleshooting.md)」を参照してください。  
  
 SQL Server 2016 RC1 から RC2 または RC3 にアップグレードすると、クエリは失敗する場合があります。 詳細と救済方法については、「 [SQL Server 2016 リリース ノート](../../sql-server/sql-server-2016-release-notes.md) 」を参照し、"PolyBase" を検索してください。  
  
## <a name="next-steps"></a>次の手順  
 スケールアウト機能の詳細については、「 [PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)」を参照してください。  PolyBase を監視するには、「 [PolyBase のトラブルシューティング](../../relational-databases/polybase/polybase-troubleshooting.md)」を参照してください。 PolyBase パフォーマンスのトラブルシューティングについては、「[PolyBase troubleshooting with dynamic management views (動的管理ビューを使用した PolyBase のトラブルシューティング)](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)   
 [PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)   
 [PolyBase ストアド プロシージャ](http://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
