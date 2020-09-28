---
title: Erstellen eines Ressourcenpools
description: Erfahren Sie, wie Sie einen Ressourcenpool für die Verwaltung von Python- und R-Workloads in SQL Server Machine Learning Services erstellen und verwenden können.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 08/06/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 08f2c66fec80ce27e3e7a9ffca7a00194ff3b81b
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283761"
---
# <a name="create-a-resource-pool-for-sql-server-machine-learning-services"></a>Erstellen eines Benutzerkontenpools für SQL Server Machine Learning Services
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Erfahren Sie, wie Sie einen Ressourcenpool für die Verwaltung von Python- und R-Workloads in SQL Server Machine Learning Services erstellen und verwenden können. 

Der Prozess umfasst mehrere Schritte:

1. Überprüfen des Status aller vorhandenen Ressourcenpools Es ist wichtig, dass Sie verstehen, welche Dienste vorhandene Ressourcen verwenden.
2. Ändern der Serverressourcenpools
3. Erstellen eines neuen Ressourcenpools für externe Prozesse
4. Erstellen einer Klassifizierungsfunktion, um R-Anforderungen zu identifizieren
5. Überprüfen, dass der externe Ressourcenpool R- oder Python-Aufträge von den angegebenen Clients oder Konten erfasst

<a name="bkmk_ReviewStatus"></a>

##  <a name="review-the-status-of-existing-resource-pools"></a>Überprüfen des Status der vorhandenen Ressourcenpools
  
1.  Verwenden Sie eine Anweisung wie die folgende, um die Ressourcen zu überprüfen, die dem Standardpool für den Server zugewiesen sind.
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **Beispielergebnisse**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|default|0|100|0|100|100|0|0|

2.  Überprüfen Sie die Ressourcen, die dem **externen** Standardressourcenpool zugewiesen sind.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **Beispielergebnisse**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|default|100|20|0|2|
 
3.  Angesichts dieser Serverstandardeinstellungen wird die externe Runtime wahrscheinlich nicht über ausreichend Ressourcen verfügen, um die meisten Aufgaben abzuschließen. Um die Ressourcen zu optimieren, müssen Sie die Nutzung der Serverressourcen wie folgt ändern:
  
    -   Reduzieren Sie den maximalen Arbeitsspeicher, der von der Datenbank-Engine verwendet werden kann.
  
    -   Erhöhen Sie den maximalen Arbeitsspeicher, der vom externen Prozess verwendet werden kann.

## <a name="modify-server-resource-usage"></a>Ändern der Nutzung von Serverressourcen

1.  Führen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] folgende Anweisung aus, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Arbeitsspeicherauslastung auf **60%** des Werts in der Einstellung „max Server Memory“ zu begrenzen.

    ```sql
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);
    ```
  
2. Führen Sie die folgende Anweisung aus, um die Verwendung des Arbeitsspeichers durch externe Prozesse auf **40 %** der gesamten Computerressourcen zu begrenzen.
  
    ```sql
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);
    ```
  
3.  Um diese Änderung zu erzwingen, müssen Sie die Ressourcenkontrolle wie folgt neu konfigurieren und neu starten:
  
    ```sql
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
    > [!NOTE]
    >  Dies sind lediglich empfohlene Einstellungen, mit denen Sie beginnen können. Sie sollten die Machine Learning-Tasks jedoch anhand anderer Serverprozesse bewerten, um das richtige Gleichgewicht für Ihre Umgebung und Arbeitsauslastung bestimmen zu können.

## <a name="create-a-user-defined-external-resource-pool"></a>Erstellen eines benutzerdefinierten externen Ressourcenpools
  
1.  Alle Änderungen an der Konfiguration von Resource Governor werden auf dem gesamten Server erzwungen. Die Änderungen betreffen sowohl Workloads, die die Standardpools für den Server verwenden, als auch Workloads, die die externen Pools verwenden.
  
     Um eine präzisere Kontrolle bereitzustellen, bei der Arbeitslasten Vorrang haben, können Sie einen neuen benutzerdefinierten externen Ressourcenpool erstellen. Definieren Sie eine Klassifizierungsfunktion, und weisen Sie sie dem externen Ressourcenpool zu. Das Schlüsselwort **EXTERN** ist neu.
  
     Erstellen Sie einen neuen *benutzerdefinierten externen Ressourcenpool*. Im folgenden Beispiel erhält der Pool den Namen **ds_ep**.
  
    ```sql
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);
    ```

2.  Erstellen Sie eine Arbeitsauslastungsgruppe mit dem Namen `ds_wg`, die Sie für die Verwaltung von Sitzungsanforderungen verwenden. Verwenden Sie für SQL-Abfragen den Standardpool und für alle externen Prozessabfragen den `ds_ep`-Pool.
  
    ```sql
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";
    ```
  
     Anforderungen werden der Standardgruppe zugewiesen, wenn die Anforderung nicht klassifiziert werden kann, oder wenn ein sonstiger Klassifizierungsfehler aufgetreten ist.

 
Weitere Informationen finden Sie unter [Resource Governor Workload Group (Arbeitsauslastungsgruppe der Ressourcenkontrolle)](../../relational-databases/resource-governor/resource-governor-workload-group.md) und [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md).
  
## <a name="create-a-classification-function-for-machine-learning"></a>Erstellen einer Klassifizierungsfunktion für Machine Learning
  
Eine Klassifizierungsfunktion untersucht eingehende Aufgaben. Sie bestimmt, ob die Aufgabe mithilfe des aktuellen Ressourcenpools ausgeführt werden kann. Aufgaben, die die Kriterien der Klassifizierungsfunktion nicht erfüllen, werden wieder an den Standardressourcenpool des Servers zurückgewiesen.
  
1. Beginnen Sie mit der Angabe, dass eine Klassifizierungsfunktion vom Resource Governor verwendet werden soll, um Ressourcenpools zu bestimmen. Sie können einen **NULL**-Wert als Platzhalter für die Klassifizierungsfunktion zuweisen.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     Weitere Informationen finden Sie unter [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).
  
2.  Definieren Sie in der Klassifizierungsfunktion für jeden Ressourcenpool den Typ der Anweisung oder der eingehenden Anforderungen, die dem Ressourcenpool zugewiesen werden soll.
  
     Beispielsweise gibt die folgende Funktion den Namen des Schemas zurück, das dem benutzerdefinierten externen Ressourcenpool zugewiesen wurde, wenn es sich bei der Anwendung, die die Anforderung gesendet hat, um „Microsoft R Host“, „RStudio“ oder „Mashup“ handelt. Andernfalls wird der Standardressourcenpool zurückgegeben.
  
    ```sql
    USE master
    GO
    CREATE FUNCTION is_ds_apps()
    RETURNS sysname
    WITH schemabinding
    AS
    BEGIN
        IF program_name() in ('Microsoft R Host', 'RStudio', 'Mashup') RETURN 'ds_wg';
        RETURN 'default'
        END;
    GO
    ```
  
3.  Konfigurieren Sie nach dem Erstellen der Funktion die Ressourcengruppe, um die neue Klassifizierungsfunktion der externen Ressourcengruppe zuweisen, die Sie zuvor definiert haben.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    GO
    ```

## <a name="verify-new-resource-pools-and-affinity"></a>Überprüfen des neuen Ressourcenpools und der Affinität

Überprüfen Sie die Arbeitsspeicherkonfiguration und die CPU des Servers für jede der Workloadgruppen. Prüfen Sie, ob die Änderungen an der Instanzressource vorgenommen wurden, indem Sie Folgendes überprüfen:

+ der Standardpool für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Server
+ der Standardressourcenpool für externe Prozesse
+ der benutzerdefinierte Pool für externe Prozesse

1. Führen Sie folgende Anweisung aus, um alle Arbeitsauslastungsgruppen anzuzeigen:

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **Bespielergebnisse**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |1|internal|Medium|25|0|0|0|0|1|2|
    |2|default|Medium|25|0|0|0|0|2|2|
    |256|ds_wg|Medium|25|0|0|0|0|2|256|
  
2.  Verwenden Sie die neue Katalogsicht [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), um alle externen Ressourcenpools anzuzeigen.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **Bespielergebnisse**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|Version|
    |-|-|-|-|-|-|
    |2|default|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     Weitere Informationen finden Sie unter [Resource Governor Catalog Views &#40;Transact-SQL&#41; (Resource Governor-Katalogsichten (Transact-SQL))](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).
  
3.  Führen Sie gegebenenfalls die folgende Anweisung aus, um Informationen zu den Ressourcen des Computers zurückzugeben, die dem externen Ressourcenpool zugeordnet sind:
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     Es werden keine Informationen angezeigt, da die Pools mit einer Affinität „AUTO“ erstellt wurden. Weitere Informationen finden Sie unter [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Verwalten von Serverressourcen finden Sie hier:

+ [Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md) 
+ [Dynamische Verwaltungssichten in Verbindung mit dem Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

Eine Übersicht über die Ressourcenkontrolle für Machine Learning finden Sie unter:

+ [Verwalten von Python- und R-Arbeitsauslastungen mit dem Resource Governor in SQL Server Machine Learning Services](resource-governor.md)
