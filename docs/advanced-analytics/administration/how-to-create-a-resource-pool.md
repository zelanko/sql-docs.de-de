---
title: 'Gewusst wie: Erstellen eines Ressourcenpools für R und Python - SQL Server Machine Learning Services'
description: Definieren Sie einen SQL Server-Ressourcenpool für R oder Python-Prozesse auf eine SQL Server 2016 oder SQL Server 2017-Datenbank-Engine-Instanz.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3f032a9e2a60a0428a2aac76ae8c3ee6baa62775
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963151"
---
# <a name="how-to-create-a-resource-pool-for-machine-learning-in-sql-server"></a>Gewusst wie: Erstellen Sie einen Ressourcenpool für Machine Learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, wie Sie erstellen und verwenden einen Ressourcenpool speziell für die Verwaltung von R und Python Machine Learning-Workloads in SQL Server. Es wird davon ausgegangen, dass Sie bereits installiert und aktiviert die Machine learning-Funktionen, und die Instanz, um eine differenziertere Verwaltung der Ressourcen von externen Prozess wie R oder Python-Unterstützung neu konfigurieren möchten.

Der Prozess umfasst mehrere Schritte:

1.  Überprüfen Sie Status, der alle vorhandenen Ressourcenpools. Es ist wichtig, dass Sie verstehen, welche Dienste die vorhandene Ressourcen verwendet werden.
2.  Ändern Sie die Server-Ressourcenpools.
3.  Erstellen Sie einen neuen Ressourcenpool für externe Prozesse.
4.  Erstellen Sie eine Klassifizierungsfunktion, die zum Identifizieren von externen skriptanforderungen.
5.  Stellen Sie sicher, dass der neue externe Ressourcenpool R oder Python-Aufträge aus der angegebenen Clients oder Konten erfasst.

##  <a name="bkmk_ReviewStatus"></a>Überprüfen des Status der vorhandenen Ressourcenpools
  
1.  Verwenden Sie eine Anweisung ähnlich der folgenden, um die Ressourcen, die zugeordnet wird, um den Standardpool für den Server zu überprüfen.
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **Beispielergebnisse**

    |pool_id|NAME|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|default|0|100|0|100|100|0|0|

2.  Überprüfen Sie die Ressourcen, die dem **externen** Standardressourcenpool zugeordnet sind.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **Beispielergebnisse**

    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|default|100|20|0|2|
 
3.  Unter dieser Serverstandardeinstellungen müssen die externe Laufzeit wahrscheinlich nicht genügend Ressourcen, die meisten Aufgaben abzuschließen. Um dies zu ändern, müssen Sie die Nutzung der Serverressourcen wie folgt ändern:
  
    -   Reduzieren des maximalen Arbeitsspeichers, die von der Datenbank-Engine verwendet werden kann.
  
    -   Erhöhen des maximalen Arbeitsspeichers, die von den externen Prozess verwendet werden kann.

## <a name="modify-server-resource-usage"></a>Ändern der Nutzung von Serverressourcen

1.  Führen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] folgende Anweisung aus, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Arbeitsspeicherauslastung auf **60%** des Werts in der Einstellung „max Server Memory“ zu begrenzen.

    ```sql
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);
    ```
  
2.  Führen Sie analog dazu die folgende Anweisung aus, um die Verwendung des Arbeitsspeichers durch externe Prozesse auf **40%** der gesamten Computerressourcen zu begrenzen.
  
    ```sql
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);
    ```
  
3.  Um diese Änderung zu erzwingen, müssen Sie die Ressourcenkontrolle wie folgt neu konfigurieren und neu starten:
  
    ```sql
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
    > [!NOTE]
    >  Dies sind lediglich empfohlene Einstellungen, mit. Sie sollten Ihre Machine learning-Aufgaben Hinblick auf andere Serverprozesse auf das richtige Gleichgewicht für Ihre Umgebung und Arbeitslast bestimmen bewerten.

## <a name="create-a-user-defined-external-resource-pool"></a>Erstellen eines benutzerdefinierten externen Ressourcenpools
  
1.  Jede Änderung an der Konfiguration der Ressourcenkontrolle betrifft den Server als Ganzes und wirkt sich auf Arbeitslasten aus, die die Standardpools für den Server verwenden, sowie auf Arbeitslasten, die die externen Pools verwenden.
  
     Um eine präzisere Kontrolle bereitzustellen, bei der Arbeitslasten Vorrang haben, können Sie einen neuen benutzerdefinierten externen Ressourcenpool erstellen. Sie sollten zudem auch eine Klassifizierungsfunktion definieren und sie dem externen Ressourcenpool zuweisen. Die **externe** Schlüsselwort ist neu.
  
     Erstellen Sie zunächst einen neuen *benutzerdefinierten externen Ressourcenpool*. Im folgenden Beispiel erhält der Pool den Namen **ds_ep**.
  
    ```sql
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);
    ```

2.  Erstellen Sie eine Arbeitsauslastungsgruppe mit dem Namen `ds_wg`, die Sie für die Verwaltung von Sitzungsanforderungen verwenden. Verwenden Sie für SQL-Abfragen den Standardpool und für alle externen Prozessabfragen den `ds_ep`-Pool.
  
    ```sql
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";
    ```
  
     Anforderungen werden der Standardgruppe zugewiesen, wenn die Anforderung nicht klassifiziert werden kann, oder wenn ein sonstiger Klassifizierungsfehler aufgetreten ist.
  
     Weitere Informationen finden Sie unter [Resource Governor Workload Group (Arbeitsauslastungsgruppe der Ressourcenkontrolle)](../../relational-databases/resource-governor/resource-governor-workload-group.md) und [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md).
  
## <a name="create-a-classification-function-for-machine-learning"></a>Erstellen einer Klassifizierungsfunktion für Machine learning
  
Eine Klassifizierungsfunktion untersucht eingehenden Aufgaben und bestimmt, ob sie mithilfe des aktuellen Ressourcenpools ausgeführt werden können. Aufgaben, die die Kriterien der Klassifizierungsfunktion nicht erfüllen, werden wieder an den Standardressourcenpool des Servers zurückgewiesen.
  
1. Zunächst gibt an, dass eine Klassifizierungsfunktion der Ressourcenkontrolle verwendet werden soll um Ressourcenpools zu bestimmen. Sie können Zuweisen einer **null** als Platzhalter für die Klassifizierungsfunktion.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     Weitere Informationen finden Sie unter [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).
  
2.  Definieren Sie in der Klassifizierungsfunktion zu jedem Ressourcenpool den Typ der Anweisung oder eingehende Anforderungen, die dem Ressourcenpool zugewiesen werden soll.
  
     Beispielsweise gibt die folgende Funktion den Namen des Schemas zurück, der dem benutzerdefinierten externen Ressourcenpool zugewiesen wurde, wenn es sich bei der Anwendung, die die Anforderung gesendet wird, um Microsoft R Host oder RStudio handelt. Andernfalls wird der Standardressourcenpool zurückgegeben.
  
    ```sql
    USE master
    GO
    CREATE FUNCTION is_ds_apps()
    RETURNS sysname
    WITH schemabinding
    AS
    BEGIN
        IF program_name() in ('Microsoft R Host', 'RStudio') RETURN 'ds_wg';
        RETURN 'default'
        END;
    GO
    ```
  
3.  Konfigurieren Sie nach dem Erstellen der Funktion die Ressourcengruppe, um die neue Klassifizierungsfunktion der externen Ressourcengruppe zuweisen, die Sie zuvor definiert haben.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);
    ALTER RESOURCE GOVERNOR WITH reconfigure;
    GO
    ```

## <a name="verify-new-resource-pools-and-affinity"></a>Überprüfen des neuen Ressourcenpools und der Affinität

Um sicherzustellen, dass die Änderungen vorgenommen wurden, sollten Sie die Konfiguration der Serverarbeitsspeicher und CPU für den Workload-Gruppen, die diese Instanz-Ressourcenpools zugeordnet überprüfen:

+ der Standardpool für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Server
+ der standardressourcenpool für externe Prozesse
+ die benutzerdefinierten Pool für externe Prozesse

1. Führen Sie die folgende Anweisung aus, um alle Arbeitsauslastungsgruppen anzuzeigen:

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **Beispielergebnisse**

    |group_id|NAME|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |1|internal|Mittel|25|0|0|0|0|1|2|
    |2|default|Mittel|25|0|0|0|0|2|2|
    |256|ds_wg|Mittel|25|0|0|0|0|2|256|
  
2.  Verwenden Sie die neue Katalogsicht [Sys. resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), um alle externen Ressourcenpools anzuzeigen.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **Beispielergebnisse**
    
    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|default|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     Weitere Informationen finden Sie unter [Resource Governor Catalog Views &#40;Transact-SQL&#41; (Resource Governor-Katalogsichten (Transact-SQL))](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).
  
3.  Führen Sie die folgende Anweisung zum Zurückgeben von Informationen zu den Ressourcen des Computers, die in den externen Ressourcenpool zugeordnet sind, falls zutreffend:
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     Da die Pools mit der Affinität „AUTO“ erstellt wurden, wird in diesem Fall keine Informationen angezeigt. Weitere Informationen finden Sie unter [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).

## <a name="see-also"></a>Siehe auch

Weitere Informationen zum Verwalten von Serverressourcen finden Sie unter:

+  [Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md) 
+ [Dynamische Verwaltungssichten in Verbindung mit der Ressourcenkontrolle &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

Einen Überblick über die Ressourcenkontrolle für Machine learning finden Sie unter:

+  [Ressourcenkontrolle für Machine Learning-Dienste](../../advanced-analytics/r/resource-governance-for-r-services.md)
