---
title: Erstellen ein benutzerdefinierten Sammlungssatzes, der den generischen T-SQL-Abfragesammlertyp (Transact-SQL) verwendet. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- T-SQL Query collector type
- collection sets [SQL Server], creating custom
ms.assetid: 6b06db5b-cfdc-4ce0-addd-ec643460605b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5c131f413c8b7be0dad8432c5711b19e74253aab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873336"
---
# <a name="create-a-custom-collection-set-that-uses-the-generic-t-sql-query-collector-type-transact-sql"></a>Erstellen eines benutzerdefinierten Sammlungssatzes, der einen generischen T-SQL-Abfragesammlertyp verwendet (Transact-SQL)
  Sie können auch mithilfe der mit dem Datensammler bereitgestellten gespeicherten Prozeduren einen benutzerdefinierten Sammlungssatz mit Sammelelementen erstellen, die den generischen T-SQL-Abfragesammlertyp verwenden. Das Ausführen dieses Tasks umfasst die Verwendung des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um die folgenden Vorgänge durchzuführen:  
  
-   Konfigurieren von Uploadzeitplänen  
  
-   Definieren und Erstellen des Sammlungssatzes  
  
-   Definieren und Erstellen eines Auflistelements  
  
-   Überprüfen, ob der Sammlungssatz und die Sammelelemente vorhanden sind.  
  
> [!NOTE]  
>  Bevor Sie einen benutzerdefinierten Sammlungssatz erstellen, müssen Sie Datensammlungsparameter konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von Parametern für die Datensammlung &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md).  
  
### <a name="define-and-create-the-collection-set"></a>Definieren und Erstellen des Sammlungssatzes  
  
1.  Definieren Sie mit der gespeicherten Prozedur „sp_syscollector_create_collection_set“ einen neuen Sammlungssatz.  
  
    ```  
    USE msdb;  
    DECLARE @collection_set_id int;  
    DECLARE @collection_set_uid uniqueidentifier;  
    EXEC sp_syscollector_create_collection_set   
        @name=N'DMV Test 1',   
        @collection_mode=0,   
        @description=N'This is a test collection set',   
        @logging_level=1,   
        @days_until_expiration=14,   
        @schedule_name=N'CollectorSchedule_Every_15min',   
        @collection_set_id=@collection_set_id OUTPUT,   
        @collection_set_uid=@collection_set_uid OUTPUT;  
    SELECT @collection_set_id, @collection_set_uid;  
    ```  
  
     Der Auflistmodus kann auf 0 (zwischengespeichert) oder 1 (nicht zwischengespeichert) festgelegt werden.  
  
     Der Protokolliergrad kann auf 0, 1 oder 2 festgelegt werden.  
  
     Die folgenden vorkonfigurierten Zeitpläne werden mit dem Datensammler bereitgestellt:  
  
    -   CollectorSchedule_Every_5min  
  
    -   CollectorSchedule_Every_10min  
  
    -   CollectorSchedule_Every_15min  
  
    -   CollectorSchedule_Every_30min  
  
    -   CollectorSchedule_Every_60min  
  
    -   CollectorSchedule_Every_6h  
  
     Wenn Sie keinen der bereitgestellten Zeitpläne verwenden möchten, können Sie einen neuen Zeitplan erstellen und für den Sammlungssatz verwenden. Weitere Informationen finden Sie unter [Anlegen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
### <a name="define-and-create-a-collection-item"></a>Definieren und Erstellen eines Auflistelements  
  
1.  Da das neue Sammelelement auf einem generischen Sammlertyp basiert, der bereits installiert ist, können Sie den folgenden Code ausführen, um die GUID so festzulegen, dass Sie dem generischen T-SQL-Abfragesammlertyp entspricht.  
  
    ```sql  
    DECLARE @collector_type_uid uniqueidentifier;  
    SELECT @collector_type_uid = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
    WHERE name = N'Generic T-SQL Query Collector Type';  
    DECLARE @collection_item_id int;  
    ```  
  
2.  Verwenden Sie die gespeicherte Prozedur „sp_syscollector_create_collection_item“, um das Sammelelement zu erstellen. Deklarieren Sie das Schema für das Auflistelement so, dass es dem Schema zugeordnet wird, das für den generischen T-SQL-Abfragesammlertyp erforderlich ist.  
  
    ```sql  
    EXEC sp_syscollector_create_collection_item   
        @name=N'Query Stats - Test 1',   
        @parameters=N'  
            <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
            <Value>SELECT * FROM sys.dm_exec_query_stats</Value>  
            <OutputTable>dm_exec_query_stats</OutputTable>  
            </Query>  
            </ns:TSQLQueryCollector>',   
        @collection_item_id=@collection_item_id OUTPUT,   
        @frequency=5,   
        @collection_set_id=@collection_set_id,   
        @collector_type_uid=@collector_type_uid;  
    SELECT @collection_item_id;  
    ```  
  
### <a name="verify-that-the-new-collection-set-and-collection-item-exist"></a>Überprüfen, ob der neue Sammlungssatz und das Sammelelement vorhanden sind  
  
1.  Bevor Sie den neuen Sammlungssatz starten, führen Sie die folgende Abfrage aus, um zu überprüfen, dass der neue Sammlungssatz und sein Auflistelement erstellt wurden.  
  
    ```sql  
    USE msdb;  
    SELECT * FROM syscollector_collection_sets;  
    SELECT * FROM syscollector_collection_items;  
    GO  
    ```  
  
     Sie können auch eine visuelle Prüfung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]durchführen. Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** , und erweitern Sie dann **Datensammlung**. Der neue Sammlungssatz wird angezeigt. Das rote Kreissymbol für den Sammlungssatz gibt an, dass der Sammlungssatz beendet wurde.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden die in den vorherigen Schritten dokumentierten Beispiele miteinander kombiniert. Beachten Sie, dass die für das Sammelelement festgelegte Auflistungshäufigkeit (5 Sekunden) ignoriert wird, da der Auflistungsmodus des Sammlungssatzes auf 0 festgelegt ist, was dem Modus mit Zwischenspeicherung entspricht. Weitere Informationen finden Sie unter [Data Collection](data-collection.md).  
  
```sql  
USE msdb;  
  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier  
  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'DMV Stats Test 1',  
    @collection_mode = 0,  
    @description = N'This is a test collection set',  
    @logging_level=1,  
    @days_until_expiration = 14,  
    @schedule_name=N'CollectorSchedule_Every_15min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
SELECT @collection_set_id,@collection_set_uid;  
  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = collector_type_uid FROM syscollector_collector_types   
WHERE name = N'Generic T-SQL Query Collector Type';  
  
DECLARE @collection_item_id int;  
EXEC sp_syscollector_create_collection_item  
@name= N'Query Stats - Test 1',  
@parameters=N'  
<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
<Query>  
  <Value>select * from sys.dm_exec_query_stats</Value>  
  <OutputTable>dm_exec_query_stats</OutputTable>  
</Query>  
 </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 5, -- This parameter is ignored in cached mode  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = @collector_type_uid;  
SELECT @collection_item_id;  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)   
 [Zeitpläne verwalten](../../ssms/agent/manage-schedules.md)   
 [Starten oder Beenden eines Sammlungssatzes](start-or-stop-a-collection-set.md)  
  
  
