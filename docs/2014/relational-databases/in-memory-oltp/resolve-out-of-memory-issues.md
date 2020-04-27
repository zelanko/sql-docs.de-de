---
title: Beheben von OOM-Problemen (nicht genügend Arbeitsspeicher) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e31f36624e8923722612810836df5d2a57b6b686
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67624407"
---
# <a name="resolve-out-of-memory-issues"></a>Beheben von OOM-Problemen (nicht genügend Arbeitsspeicher)
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] verwendet mehr Arbeitsspeicher und nutzt diesen auf andere Weise als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Es kann vorkommen, dass der installierte, [!INCLUDE[hek_2](../../includes/hek-2-md.md)] zugeordnete Arbeitsspeicher Ihren wachsenden Anforderungen nicht mehr gerecht wird, sodass kein ausreichender Arbeitsspeicher zur Verfügung steht. In diesem Thema erfahren Sie, wie Sie OOM-Situationen (Out of Memory, nicht genügend Arbeitsspeicher) beheben. Weitere Hinweise zur Vermeidung von Situationen mit unzureichendem Arbeitsspeicher finden Sie auch unter dem Thema [Überwachung und Problembehebung bei der Arbeitsspeichernutzung](monitor-and-troubleshoot-memory-usage.md) .  
  
## <a name="covered-in-this-topic"></a>In diesem Thema  
  
|Thema|Übersicht|  
|-----------|--------------|  
| [Beheben von Fehlern aufgrund von OOM-Bedingungen bei der Datenbankwiederherstellung](#resolve-database-restore-failures-due-to-oom) |Erläutert, wie Sie bei der Fehlermeldung „Fehler beim Wiederherstellungsvorgang für Datenbank „ *\<Datenbankname>* “ aufgrund von unzureichendem Arbeitsspeicher im Ressourcenpool „ *\<Ressourcenpoolname>* “ vorgehen.|  
| [Beheben von Beeinträchtigungen der Arbeitsauslastung durch wenig oder unzureichenden Arbeitsspeicher](#resolve-impact-of-low-memory-or-oom-conditions-on-the-workload)|Erläutert, wie Sie vorgehen, wenn die Leistung durch unzureichenden Arbeitsspeicher beeinträchtigt wird.|  
| [Beheben von Seitenzuordnungsfehlern aufgrund von unzureichendem Arbeitsspeicher, obwohl ausreichend Arbeitsspeicher verfügbar ist](#resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available) |Erläutert, wie Sie bei der Fehlermeldung „Seitenbelegungen für die Datenbank „ *\<Datenbankname>* “ sind aufgrund unzureichenden Arbeitsspeichers im Ressourcenpool „ *\<Ressourcenpoolname>* “ nicht zulässig“ vorgehen. … nicht zugelassen“ vorgehen, wenn ausreichend Arbeitsspeicher für den Vorgang verfügbar ist.|  
  
## <a name="resolve-database-restore-failures-due-to-oom"></a>Beheben von Fehlern aufgrund von OOM-Bedingungen bei der Datenbankwiederherstellung  
 Wenn Sie versuchen, eine Datenbank wiederherzustellen, erhalten Sie möglicherweise die folgende Fehlermeldung: "Fehler beim Wiederherstellungs Vorgang für die Datenbank"*\<DatabaseName>*"aufgrund von unzureichendem Arbeitsspeicher im Ressourcenpool"*\<ResourcePoolName>*". Bevor Sie die Datenbank erfolgreich wiederherstellen können, müssen Sie das Problem beim unzureichenden Arbeitsspeicher beheben, indem Sie mehr Arbeitsspeicher zur Verfügung stellen.  
  
 Um Wiederherstellungsfehler aufgrund von OOM-Bedingungen zu beheben, erhöhen Sie den verfügbaren Arbeitsspeicher durch einige oder alle diese Maßnahmen zum vorübergehenden Erhöhen des für den Wiederherstellungsvorgang verfügbaren Arbeitsspeichers.  
  
-   Schließen Sie ausgeführte Anwendungen vorübergehend.   
    Indem Sie eine oder mehrere ausgeführte Anwendungen, wie Visual Studio, Internet Explorer, OneNote und andere, schließen, geben Sie den von den Anwendungen belegten Arbeitsspeicher für den Wiederherstellungsvorgang frei. Nach der erfolgreichen Wiederherstellung können Sie sie wieder starten.  
  
-   Erhöhen Sie den Wert von MAX_MEMORY_PERCENT.   
    In diesem Codeausschnitt wird MAX_MEMORY_PERCENT für den PoolHk-Ressourcenpool in 70 % des installierten Arbeitsspeichers geändert.  
  
    > [!IMPORTANT]  
    >  Wenn der Server auf einem virtuellen Computer ausgeführt wird und nicht dediziert ist, legen Sie den Wert von MIN_MEMORY_PERCENT auf denselben Wert wie MAX_MEMORY_PERCENT fest.   
    > Weitere Informationen finden [Sie im Thema bewährte Methoden: Verwenden von in-Memory-OLTP in einer VM-Umgebung](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) .  
  
    ```sql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     Informationen zu den maximalen Werten für MAX_MEMORY_PERCENT finden Sie im Abschnitt [Prozentsatz des verfügbaren Arbeitsspeichers für Speicher optimierte Tabellen und Indizes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes) .
  
-   Konfigurieren Sie **Max. Serverarbeitsspeicher** neu.  
    Informationen zum Konfigurieren von **Max. Serverarbeitsspeicher** finden Sie unter dem Thema [Optimieren der Serverleistung mithilfe von Speicherkonfigurationsoptionen](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).  
  
## <a name="resolve-impact-of-low-memory-or-oom-conditions-on-the-workload"></a>Beheben von Beeinträchtigungen der Arbeitsauslastung durch wenig oder unzureichenden Arbeitsspeicher  
 Grundsätzlich sind Situationen mit wenig oder unzureichendem Arbeitsspeicher zu vermeiden. Häufig lassen sich OOM-Situationen durch eine durchdachte Planung und Überwachung vermeiden. Aber auch die beste Planung schützt nicht vor unvorhersehbaren Ereignissen, die zu knappem oder unzureichendem Arbeitsspeicher führen können. Eine OOM-Bedingung kann in zwei Schritten behoben werden:  
  
1.  [Öffnen einer DAC (dedizierte Administratorverbindung)](#open-a-dac-dedicated-administrator-connection) 
  
2.  [Korrekturmaßnahme](#take-corrective-action) 
  
### <a name="open-a-dac-dedicated-administrator-connection"></a>Öffnen einer DAC (dedizierte Administratorverbindung)  
 Microsoft SQL Server bietet eine dedizierte Administratorverbindung (Dedicated Administrator Connection, DAC). Mit der DAC können Administratoren auf eine ausgeführte Instanz der SQL Server-Datenbank-Engine zugreifen, um Probleme auf dem Server zu beheben, selbst wenn der Server auf andere Clientverbindungen nicht reagiert. Die DAC ist über das `sqlcmd` -Hilfsprogramm und SQL Server Management Studio (SSMS) verfügbar.  
  
 Anweisungen zur Verwendung von `sqlcmd` und einer DAC finden Sie unter [Verwenden einer dedizierten Administratorverbindung](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md). Anweisungen zur Verwendung der DAC über SSMS finden Sie unter [Vorgehensweise: Verwenden der dedizierten Administratorverbindung mit SQL Server Management Studio](https://msdn.microsoft.com/library/ms178068.aspx).  
  
### <a name="take-corrective-action"></a>Korrekturmaßnahme  
 Um die OOM-Bedingung zu beheben, müssen Sie entweder vorhandenen Arbeitsspeicher freigeben, indem Sie die Arbeitsspeichernutzung reduzieren, oder den Tabellen im Arbeitsspeicher mehr Arbeitsspeicherkapazität zur Verfügung stellen.  
  
#### <a name="free-up-existing-memory"></a>Freigeben von vorhandenem Arbeitsspeicher  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a>Löschen unwichtiger Zeilen aus speicheroptimierten Tabellen und Abwarten der Garbage Collection  
 Sie können unbedeutende Zeilen aus einer speicheroptimierten Tabelle entfernen. Der Garbage Collector gibt den von diesen Zeilen belegten Speicher wieder an den verfügbaren Arbeitsspeicher zurück. . Garbage-Zeilen werden von der In-Memory-OLTP-Engine auf aggressive Weise gesammelt. Allerdings kann die Garbage Collection durch eine Transaktion mit langer Ausführungszeit verhindert werden. Beispiel: Bei einer Transaktion, die fünf Minuten ausgeführt wird, kann für Zeilenversionen, die aufgrund von Update-/Löschvorgängen erstellt wurden, während die Transaktion aktiv war, keine Garbage Collection ausgeführt werden.  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a>Verschieben einer oder mehrerer Zeilen in eine datenträgerbasierte Tabelle  
 In den folgenden TechNet-Artikeln finden Sie Richtlinien zum Verschieben von Zeilen aus einer speicheroptimierten Tabelle in eine datenträgerbasierte Tabelle.  
  
-   [Partitionierung auf Anwendungsebene](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)  
  
-   [Anwendungsmuster zur Partitionierung von speicheroptimierten Tabellen](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)  
  
#### <a name="increase-available-memory"></a>Erhöhen der verfügbaren Arbeitsspeicherkapazität  
  
##### <a name="increase-value-of-max_memory_percent-on-the-resource-pool"></a>Erhöhen des MAX_MEMORY_PERCENT-Werts für den Ressourcenpool  
 Wenn Sie keinen benannten Ressourcenpool für die Tabellen im Arbeitsspeicher erstellt haben, sollten Sie dies nachholen und die [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -Datenbanken daran binden. Im Thema [Binden einer Datenbank mit speicheroptimierten Tabellen an einen Ressourcenpool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) finden Sie eine Anleitung zum Erstellen und Binden Ihrer [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -Datenbanken an einen Ressourcenpool.  
  
 Wenn die [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -Datenbank an einen Ressourcenpool gebunden ist, können Sie den Arbeitsspeicheranteil, auf den der Pool zugreifen kann, erhöhen. Im Unterabschnitt [Ändern von MIN_MEMORY_PERCENT und MAX_MEMORY_PERCENT für einen vorhandenen Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) finden Sie entsprechende Anleitungen zum Ändern.  
  
 Erhöhen Sie den Wert von MAX_MEMORY_PERCENT.   
In diesem Codeausschnitt wird MAX_MEMORY_PERCENT für den PoolHk-Ressourcenpool in 70 % des installierten Arbeitsspeichers geändert.  
  
> [!IMPORTANT]  
>  Wenn der Server auf einem virtuellen Computer ausgeführt wird und nicht dediziert ist, legen Sie den Wert von MIN_MEMORY_PERCENT und MAX_MEMORY_PERCENT auf denselben Wert fest.   
> Weitere Informationen finden [Sie im Thema bewährte Methoden: Verwenden von in-Memory-OLTP in einer VM-Umgebung](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) .  
  
```sql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 Weitere Informationen zu maximalen Werten für MAX_MEMORY_PERCENT finden Sie im Themenabschnitt [Prozentsatz des für speicheroptimierte Tabellen und Indizes verfügbaren Arbeitsspeichers](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes).  
  
##### <a name="install-additional-memory"></a>Installieren zusätzlichen Arbeitsspeichers  
 Die beste Lösung besteht letztendlich darin, falls möglich, zusätzlichen physischen Arbeitsspeicher zu installieren. Beachten Sie in diesem Fall, dass Sie wahrscheinlich auch den Wert von MAX_MEMORY_PERCENT erhöhen können (siehe untergeordnete [Änderungs MIN_MEMORY_PERCENT und MAX_MEMORY_PERCENT in einem vorhandenen Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)), da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wahrscheinlich nicht mehr Arbeitsspeicher benötigt, sodass Sie den meisten, wenn nicht der neu installierte Arbeitsspeicher für den Ressourcenpool verfügbar machen.  
  
> [!IMPORTANT]  
>  Wenn der Server auf einem virtuellen Computer ausgeführt wird und nicht dediziert ist, legen Sie den Wert von MIN_MEMORY_PERCENT und MAX_MEMORY_PERCENT auf denselben Wert fest.   
> Weitere Informationen finden [Sie im Thema bewährte Methoden: Verwenden von in-Memory-OLTP in einer VM-Umgebung](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) .  
  
## <a name="resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available"></a>Beheben von Seitenzuordnungsfehlern aufgrund von unzureichendem Arbeitsspeicher, obwohl ausreichend Arbeitsspeicher verfügbar ist  
 Wenn Sie die Fehlermeldung "Seiten Zuordnungen für die Datenbank '*\<DatabaseName>*' aufgrund von unzureichendem Arbeitsspeicher im Ressourcenpool '*\<ResourcePoolName>*'" erhalten, erhalten Sie eine Fehlermeldung. <https://go.microsoft.com/fwlink/?LinkId=330673>Weitere Informationen finden Sie unter "". im Fehlerprotokoll erhalten, obwohl der verfügbare physische Arbeitsspeicher zum Zuordnen der Seite ausreichend ist, kann dies daran liegen, dass die Ressourcenkontrolle deaktiviert ist. Wenn die Ressourcenkontrolle deaktiviert ist, führt MEMORYBROKER_FOR_RESERVE zu einem künstlichen Mangel an Arbeitsspeicher.  
  
 Um dieses Problem zu beheben, müssen Sie die Ressourcenkontrolle aktivieren.  
  
 Weitere Informationen zu Einschränkungen sowie Anweisungen zum Aktivieren des Resource Governors mit dem Objekt-Explorer, über Eigenschaften des Resource Governors oder mit Transact-SQL finden Sie unter [Aktivieren des Resource Governors](https://technet.microsoft.com/library/bb895149.aspx) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten des Arbeitsspeichers für in-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md)   
 [Überwachen und behandeln von Problemen mit der Speicherauslastung](monitor-and-troubleshoot-memory-usage.md)   
 [Binden einer Datenbank mit Speicher optimierten Tabellen an einen Ressourcen Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [Bewährte Methoden: Verwenden von In-Memory OLTP in einer Umgebung mit virtuellen Computern](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)  
  
  
