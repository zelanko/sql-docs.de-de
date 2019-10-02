---
title: Erstellen eines Ressourcenpools für python und R
description: Erfahren Sie, wie Sie einen Ressourcenpool für die Verwaltung von Python-und R-Arbeits Auslastungen in SQL Server Machine Learning Services erstellen und verwenden können.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/01/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8e8c48665c2928a0c8133892cc0029b4bd82c4cc
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714324"
---
# <a name="create-a-resource-pool-for-sql-server-machine-learning-services"></a>Erstellen eines Ressourcenpools für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erfahren Sie, wie Sie einen Ressourcenpool für die Verwaltung von Python-und R-Arbeits Auslastungen in SQL Server Machine Learning Services erstellen und verwenden können. 

Der Prozess umfasst mehrere Schritte:

1. Überprüfen Sie den Status vorhandener Ressourcenpools. Es ist wichtig, dass Sie verstehen, welche Dienste vorhandene Ressourcen verwenden.
2. Ändern Sie Server Ressourcenpools.
3. Erstellen Sie einen neuen Ressourcenpool für externe Prozesse.
4. Erstellen Sie eine Klassifizierungs Funktion, um externe Skript Anforderungen zu identifizieren.
5. Vergewissern Sie sich, dass der neue externe Ressourcenpool R-oder python-Aufträge von den angegebenen Clients oder Konten Erfassungs basiert.

<a name="bkmk_ReviewStatus"></a>

##  <a name="review-the-status-of-existing-resource-pools"></a>Überprüfen des Status vorhandener Ressourcenpools
  
1.  Verwenden Sie eine-Anweisung wie die folgende, um die Ressourcen zu überprüfen, die dem Standard Pool für den-Server zugeordnet sind.
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **Beispiel Ergebnisse**

    |pool_id|NAME|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|default|0|100|0|100|100|0|0|

2.  Überprüfen Sie die Ressourcen, die dem **externen** Standardressourcenpool zugeordnet sind.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **Beispiel Ergebnisse**

    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|default|100|20|0|2|
 
3.  Unter diesen Server Standardeinstellungen verfügt die externe Laufzeit wahrscheinlich nicht über genügend Ressourcen, um die meisten Aufgaben abzuschließen. Um dies zu ändern, müssen Sie die Nutzung der Serverressourcen wie folgt ändern:
  
    -   Reduzieren Sie den maximalen Computer Arbeitsspeicher, der von der Datenbank-Engine verwendet werden kann.
  
    -   Vergrößern Sie den maximalen Arbeitsspeicher des Computers, der vom externen Prozess verwendet werden kann.

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
    >  Dies sind nur Empfohlene Einstellungen, mit denen Sie beginnen können. Sie sollten ihre Machine Learning-Aufgaben im Hinblick auf andere Server Prozesse evaluieren, um das richtige Gleichgewicht für Ihre Umgebung und Arbeitsauslastung zu ermitteln.

## <a name="create-a-user-defined-external-resource-pool"></a>Erstellen eines benutzerdefinierten externen Ressourcenpools
  
1.  Jede Änderung an der Konfiguration der Ressourcenkontrolle betrifft den Server als Ganzes und wirkt sich auf Arbeitslasten aus, die die Standardpools für den Server verwenden, sowie auf Arbeitslasten, die die externen Pools verwenden.
  
     Um eine präzisere Kontrolle bereitzustellen, bei der Arbeitslasten Vorrang haben, können Sie einen neuen benutzerdefinierten externen Ressourcenpool erstellen. Sie sollten zudem auch eine Klassifizierungsfunktion definieren und sie dem externen Ressourcenpool zuweisen. Das Schlüsselwort " **extern** " ist neu.
  
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
  
## <a name="create-a-classification-function-for-machine-learning"></a>Erstellen einer Klassifizierungs Funktion für Machine Learning
  
Eine Klassifizierungsfunktion untersucht eingehenden Aufgaben und bestimmt, ob sie mithilfe des aktuellen Ressourcenpools ausgeführt werden können. Aufgaben, die die Kriterien der Klassifizierungsfunktion nicht erfüllen, werden wieder an den Standardressourcenpool des Servers zurückgewiesen.
  
1. Beginnen Sie, indem Sie angeben, dass eine Klassifizierungs Funktion von Resource Governor verwendet werden soll, um Ressourcenpools zu ermitteln. Sie können **null** als Platzhalter für die Klassifizierungs Funktion zuweisen.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     Weitere Informationen finden Sie unter [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).
  
2.  Definieren Sie in der Klassifizierungs Funktion für jeden Ressourcenpool den Typ der Anweisungen oder eingehenden Anforderungen, die dem Ressourcenpool zugewiesen werden sollen.
  
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

Um zu überprüfen, ob die Änderungen vorgenommen wurden, sollten Sie die Konfiguration des Server Arbeitsspeichers und der CPU für alle Arbeits Auslastungs Gruppen überprüfen, die diesen instanzressourcenpools zugeordnet sind:

+ der Standard Pool für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Server.
+ der Standard Ressourcenpool für externe Prozesse
+ der benutzerdefinierte Pool für externe Prozesse.

1. Führen Sie folgende Anweisung aus, um alle Arbeits Auslastungs Gruppen anzuzeigen:

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **Beispiel Ergebnisse**

    |group_id|NAME|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |1|Interner Pool (internal)|Medium|25|0|0|0|0|1|2|
    |2|default|Medium|25|0|0|0|0|2|2|
    |256|ds_wg|Medium|25|0|0|0|0|2|256|
  
2.  Verwenden Sie die neue Katalog Sicht [sys. resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), um alle externen Ressourcenpools anzuzeigen.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **Beispiel Ergebnisse**
    
    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|default|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     Weitere Informationen finden Sie unter [Resource Governor Catalog Views &#40;Transact-SQL&#41; (Resource Governor-Katalogsichten (Transact-SQL))](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).
  
3.  Führen Sie die folgende Anweisung aus, um Informationen über die Computerressourcen zurückzugeben, die dem externen Ressourcenpool zugeordnet sind, sofern zutreffend:
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     Da die Pools mit der Affinität „AUTO“ erstellt wurden, wird in diesem Fall keine Informationen angezeigt. Weitere Informationen finden Sie unter [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Verwalten von Server Ressourcen finden Sie unter:

+ [Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md) 
+ [Resource Governor zugehörige dynamische Verwaltungs &#40;Sichten Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

Eine Übersicht über die Ressourcenkontrolle für Machine Learning finden Sie unter:

+ [Verwalten von Python-und R-Arbeits Auslastungen mit Resource Governor in SQL Server Machine Learning Services](resource-governor.md)
