---
description: Hinzufügen eines Sammelelements zu einem Sammlungssatz (Transact-SQL)
title: Hinzufügen eines Sammlungselements zu einem Sammlungssatz (T-SQL)
ms.date: 06/03/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection items [SQL Server]
- collection sets [SQL Server], adding items
ms.assetid: 9fe6454e-8c0e-4b50-937b-d9871b20fd13
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 8ef2d09b1ce912f73d03d3e25f8dac0169e57f8c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465479"
---
# <a name="add-a-collection-item-to-a-collection-set-transact-sql"></a>Hinzufügen eines Sammelelements zu einem Sammlungssatz (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Sie können einem vorhandenen Sammlungssatz mithilfe der mit dem Datensammler bereitgestellten gespeicherten Prozeduren ein Sammlungselement hinzufügen.  
  
 Führen Sie die folgenden Schritte mithilfe des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aus.  
  
### <a name="add-a-collection-item-to-a-collection-set"></a>Hinzufügen eines Sammelelements zu einem Sammlungssatz  
  
1.  Beenden Sie den Sammlungssatz, dem Sie das Element hinzufügen möchten, in dem Sie die gespeicherte Prozedur **sp_syscollector_stop_collection_set** ausführen. Um beispielsweise einen Sammlungssatz mit dem Namen "Test Collection Set" zu beenden, führen Sie die folgenden Anweisungen aus.  
  
    ```sql  
    USE msdb;
    DECLARE @csid int;

    SELECT @csid = collection_set_id  
      FROM syscollector_collection_sets
      WHERE name = 'Test Collection Set';

    SELECT @csid;
    EXEC dbo.sp_syscollector_stop_collection_set @collection_set_id = @csid;
    ```  
  
    > [!NOTE]  
    >  Sie können den Sammlungssatz auch durch Verwendung des Objekt-Explorers in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]beenden Weitere Informationen finden Sie unter [Starten oder Beenden eines Sammlungssatzes](../../relational-databases/data-collection/start-or-stop-a-collection-set.md).  
  
2.  Deklarieren Sie den Sammlungssatz, dem Sie das Sammelelement hinzufügen möchten. Der folgende Code bietet ein Beispiel für das Deklarieren der Sammlungssatz-ID.  
  
    ```sql  
    DECLARE @collection_set_id_1 int;

    SELECT @collection_set_id_1 = collection_set_id
      FROM [msdb].[dbo].[syscollector_collection_sets]
      WHERE name = N'Test Collection Set'; -- name of collection set  
    ```  
  
3.  Deklarieren Sie den Sammlertyp. Der folgende Code bietet ein Beispiel für das Deklarieren des generischen T-SQL-Abfragesammlertyps.  
  
    ```sql  
    DECLARE @collector_type_uid_1 uniqueidentifier;

    SELECT @collector_type_uid_1 = collector_type_uid
       FROM [msdb].[dbo].[syscollector_collector_types]
       WHERE name = N'Generic T-SQL Query Collector Type';  
    ```  
  
     Führen Sie den folgenden Code aus, um eine Liste der installierten Sammlertypen abzurufen:  
  
    ```sql  
    USE msdb;
    SELECT * from syscollector_collector_types;
    GO  
    ```  
  
4.  Führen Sie die gespeicherte Prozedur **sp_syscollector_create_collection_item** aus, um das Sammlungselement zu erstellen. Das Schema für das Sammelelement muss so deklariert werden, dass es dem erforderlichen Schema für den gewünschten Sammlertyp zugeordnet wird. Im folgenden Beispiel wird das Eingabeschema der generischen T-SQL-Abfrage verwendet.  
  
    ```sql  
    DECLARE @collection_item_id int;  

    EXEC [msdb].[dbo].[sp_syscollector_create_collection_item]   
      @name=N'OS Wait Stats', --name of collection item  
      @parameters=N'  
        <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
         <Query>  
          <Value>select * from sys.dm_os_wait_stats</Value>  
          <OutputTable>os_wait_stats</OutputTable>  
        </Query>  
        </ns:TSQLQueryCollector>',  
      @collection_item_id = @collection_item_id OUTPUT,  
      @frequency = 60,  
      @collection_set_id = @collection_set_id_1, --- Provides the collection set ID number  
      @collector_type_uid = @collector_type_uid_1; -- Provides the collector type UID  
    
    SELECT @collection_item_id;
    ```  
  
5.  Bevor Sie den aktualisierten Sammlungssatz starten, führen Sie die folgende Abfrage aus, um zu überprüfen, ob das neue Sammelelement erstellt wurde:  
  
    ```sql
    USE msdb;
    GO
    SELECT * from syscollector_collection_sets;
    SELECT * from syscollector_collection_items;
    GO  
    ```  
  
     Die Sammlungssätze und ihre Sammlungselemente werden auf der Registerkarte **Ergebnisse** angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines benutzerdefinierten Sammlungssatzes, der einen generischen T-SQL-Abfragesammlertyp verwendet &#40;Transact-SQL&#41;](../../relational-databases/data-collection/create-custom-collection-set-generic-t-sql-query-collector-type.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
