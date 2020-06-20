---
title: Erstellen einer Sitzung für erweiterte Ereignisse mit dem Abfrage-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- create extended events session
- extended events [SQL Server], create session
ms.assetid: cba0e02b-b201-4863-bf1b-9164e68e5fa8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 648370ecdd2938b6fb425955dc02da8960f884c2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934531"
---
# <a name="create-an-extended-events-session-using-query-editor"></a>Erstellen einer Sitzung für erweiterte Ereignisse mit dem Abfrage-Editor
  Eine Sitzung für erweiterte Ereignisse können Sie mit dem Abfrage-Editor erstellen, können aber auch im Objekt-Explorer eine Sitzung erstellen. In Objekt-Explorer bieten erweiterte Ereignisse zwei Benutzeroberflächen, die Sie zum Erstellen, ändern und Anzeigen von Ereignis Sitzungsdaten verwenden können: einen Assistenten, der Sie durch den Prozess der Ereignis Sitzungs Erstellung führt, und eine neue Benutzeroberfläche für Sitzungen, die Erweiterte Konfigurationsoptionen bereitstellt. Sie können Sitzungen für erweiterte Ereignisse erstellen, um die SQL Server-Ablaufverfolgung zu diagnostizieren, sodass Sie z. B. folgende Aufgaben ausführen können:  
  
-   Suchen der aufwendigsten Abfragen  
  
-   Suchen der Ursachen von Latchkonflikten  
  
-   Suchen von Abfragen, die andere Abfragen blockieren  
  
-   Behandeln des Problems übermäßiger, durch Abfrageneukompilierung verursachter CPU-Auslastung  
  
-   Problembehandlung für Deadlocks  
  
 Informationen dazu, wie Sie eine Extended Events-Sitzung mit dem Assistenten für neue Sitzung erstellen, finden Sie unter [Erstellen einer Sitzung für erweiterte Ereignisse mithilfe des Assistenten &#40;Objekt-Explorer&#41;](../ssms/object/object-explorer.md). Informationen dazu, wie Sie eine Extended Events-Sitzung mit dem Assistenten für neue Sitzung erstellen, finden Sie unter [Quick Start: Extended events in SQL Server](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) (Schnellstart: Erweiterte Ereignisse in SQL Server).  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> Berechtigungen  
 Zum Erstellen einer Sitzung für erweiterte Ereignisse müssen Sie über die ALTER ANY EVENT SESSION-Berechtigung verfügen.  
  
## <a name="creating-an-extended-events-session-using-query-editor"></a>Erstellen einer Sitzung für erweiterte Ereignisse mit dem Abfrage-Editor  
  
#### <a name="to-create-an-extended-events-session"></a>So erstellen Sie eine Sitzung für erweiterte Ereignisse  
  
1.  In der folgenden Vorgehensweise wird gezeigt, wie eine Sitzung für erweiterte Ereignisse mit dem Abfrage-Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]erstellt wird.  
  
     Bestimmen Sie, welche Ereignisse Sie in der Sitzung verwenden möchten. Um alle verfügbaren Ereignisse zusammen mit dem Schlüsselwort und dem Kanal anzuzeigen, verwenden Sie die folgende Abfrage:  
  
    > [!NOTE]  
    >  Informationen zu Schlüsselwörtern und Kanälen finden Sie unter [Pakete für erweiterte Ereignisse von SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md).  
  
    ```  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
       (  
       SELECT event_package = o.package_guid, o.description,   
       event=c.object_name, channel = v.map_value  
       FROM sys.dm_xe_objects o  
       LEFT JOIN sys.dm_xe_object_columns c ON o.name = c.object_name  
       INNER JOIN sys.dm_xe_map_values v ON c.type_name = v.name   
       AND c.column_value = cast(v.map_key AS nvarchar)  
       WHERE object_type = 'event' AND (c.name = 'CHANNEL' or c.name IS NULL)  
       ) c LEFT JOIN   
       (  
       SELECT event_package = c.object_package_guid, event = c.object_name,   
       keyword = v.map_value  
       FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
       ON c.type_name = v.name AND c.column_value = v.map_key   
       AND c.type_package_guid = v.object_package_guid  
       INNER JOIN sys.dm_xe_objects o ON o.name = c.object_name   
       AND o.package_guid = c.object_package_guid  
       WHERE object_type = 'event' AND c.name = 'KEYWORD'   
       ) k  
       ON  
       k.event_package = c.event_package AND (k.event=c.event or k.event IS NULL)  
       INNER JOIN sys.dm_xe_packages p ON p.guid = c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
2.  Fügen Sie in einem neuen Abfragefenster die folgenden Anweisungen hinzu, um eine Ereignissitzung zu erstellen, und ersetzen Sie dabei *session_name* durch den Sitzungsnamen, den Sie verwenden möchten:  
  
    > [!IMPORTANT]  
    >  In den Schritten 2 bis 6 dieser Vorgehensweise werden die einzelnen Abschnitte der Ereignissitzungsdefinition beschrieben. Sie würden alle Anweisungen vor dem Ausführen einem einzelnen Abfragefenster hinzufügen. Ein vollständiges Beispiel finden Sie in den Beispielen dieses Themas.  
  
    ```  
    CREATE EVENT SESSION session_name   
    ON SERVER  
    ```  
  
3.  Fügen Sie die Ereignisse, die Sie überwachen möchten, im Format *Paketname*.*Ereignisname*hinzu. Fügen Sie für jedes Ereignis eine Zeile wie die folgende hinzu:  
  
    ```  
    ADD EVENT package_name.event_name  
    ```  
  
     Beispiel:  
  
    ```  
    ADD EVENT sqlserver.file_read_completed,  
    ADD EVENT sqlserver.file_write_completed  
    ```  
  
4.  (Optional) Nachdem Sie ein Ereignis hinzugefügt haben, können Sie zu verwendende Aktionen hinzufügen. Sie können auch Prädikate hinzufügen. Prädikate werden verwendet, um Kriterien dafür festzulegen, wann die Ereignisinformationen vom Ziel verwendet werden sollen. Aktionen werden mit einer ACTION-Klausel hinzugefügt, Prädikate werden mit einer WHERE-Klausel hinzugefügt. Um beispielsweise eine Aktion und ein Prädikat hinzuzufügen, bei der bzw. dem der [!INCLUDE[tsql](../includes/tsql-md.md)] -Text für das -Ereignis aufgezeichnet wird und die Datei-ID gleich 1 ist, würden Sie die folgende Anweisung einschließen:  
  
    ```  
    ADD EVENT sqlserver.file_read_completed  
       (ACTION (sqlserver.sql_text)  
       WHERE file_id = 1),  
    ```  
  
    -   Um anzuzeigen, welche Aktionen verfügbar sind, verwenden Sie die folgende Abfrage:  
  
        ```  
        SELECT p.name AS 'package_name', xo.name AS 'action_name', xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'action'  
        AND (xo.capabilities & 1 = 0   
        OR xo.capabilities IS NULL)  
        ORDER BY p.name, xo.name  
        ```  
  
    -   Um anzuzeigen, welche Prädikate für ein Ereignis verfügbar sind, verwenden Sie die folgende Abfrage, und ersetzen Sie *event_name* durch den Namen des Ereignisses, für das Sie ein Prädikat hinzufügen möchten:  
  
        ```  
        SELECT *  
        FROM sys.dm_xe_object_columns  
        WHERE object_name = 'event_name'  
        AND column_type = 'data'  
        ```  
  
         Beispiel:  
  
        ```  
        SELECT *   
        FROM sys.dm_xe_object_columns   
        WHERE object_name = 'file_read_completed'  
        AND column_type = 'data'  
        ```  
  
         Beachten Sie, dass Sie auch globale Prädikatquellen hinzufügen können. Eine globale Prädikatquelle kann in einen beliebigen Prädikatausdruck verwendet werden. Um anzuzeigen, welche globalen Prädikatquellen verfügbar sind, verwenden Sie die folgende Abfrage:  
  
        ```  
        SELECT p.name AS package_name, xo.name AS predicate_name  
           , xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'pred_source'  
        ORDER BY p.name, xo.name  
        ```  
  
         Sie könnten z. B. den folgenden Prädikatausdruck verwenden, um anzugeben, dass Daten für ein Ereignis nur die ersten fünf Male, die ein Ereignis auftritt, erfasst werden sollen.  
  
        ```  
        WHERE package0.counter <= 5  
        ```  
  
5.  Fügen Sie das gewünschte Ziel hinzu, an dem die Ereignisdaten verarbeitet und verwendet werden. Verwenden Sie das folgende Format:  
  
    ```  
    ADD TARGET package_name.target_name  
    ```  
  
     Im folgenden Beispiel wird das asynchrone Dateiziel hinzugefügt:  
  
    ```  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
    ```  
  
     Um die Liste der verfügbaren Ziele anzuzeigen, verwenden Sie die folgende Abfrage:  
  
    ```  
    SELECT p.name AS 'package_name', xo.name AS 'target_name'  
       , xo.description, xo.object_type   
    FROM sys.dm_xe_objects AS xo  
    JOIN sys.dm_xe_packages AS p  
       ON xo.package_guid = p.guid  
    WHERE xo.object_type = 'target'  
    AND (xo.capabilities & 1 = 0  
    OR xo.capabilities IS NULL)  
    ORDER BY p.name, xo.name  
    ```  
  
    > [!NOTE]  
    >  Informationen zu den unterschiedlichen Zieltypen finden Sie unter [Ziele für erweiterte Ereignisse von SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
6.  Überprüfen Sie alle zusätzlichen Konfigurationsoptionen, und fügen Sie sie hinzu. Sie können Optionen konfigurieren, beispielsweise den Ereignisbeibehaltungsmodus, wie lange Ereignisse im Arbeitsspeicher gepuffert werden, oder ob die Ereignissitzung automatisch gestartet werden soll, wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gestartet wird. In diesem Thema werden die Optionen beschrieben: [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql). Beachten Sie, dass Standardwerte zugewiesen werden, wenn diese Optionen nicht angegeben werden.  
  
7.  Starten Sie die Sitzung.  
  
    > [!NOTE]  
    >  Weitere Informationen zum Anzeigen der Sitzungsergebnisse finden Sie im entsprechenden Thema für den verwendeten Zieltyp im Knoten [Ziele für erweiterte Ereignisse von SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md) der Onlinedokumentation.  
  
 Im folgenden Beispiel wird eine Sitzung für erweiterte Ereignisse mit dem Namen "IOActivity" erstellt, die die folgenden Informationen aufzeichnet:  
  
-   Ereignisdaten für abgeschlossene Dateilesevorgänge, einschließlich des zugewiesenen [!INCLUDE[tsql](../includes/tsql-md.md)] -Texts für Dateilesevorgänge, bei denen die Datei-ID gleich 1 ist.  
  
-   Ereignisdaten für abgeschlossene Dateischreibvorgänge.  
  
-   Ereignisdaten für Situationen, in denen Daten aus dem Protokollcache in die physische Protokolldatei geschrieben werden.  
  
 Die Sitzung sendet die Ausgabe an ein Dateiziel.  
  
```  
CREATE EVENT SESSION IOActivity  
ON SERVER  
  
ADD EVENT sqlserver.file_read_completed  
   (  
   ACTION (sqlserver.sql_text)  
   WHERE file_id = 1),  
ADD EVENT sqlserver.file_write_completed,  
ADD EVENT sqlserver.databases_log_flush  
  
ADD TARGET package0.asynchronous_file_target   
   (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Ereignis Sitzung &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [Ziele für erweiterte Ereignisse SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [Pakete für erweiterte Ereignisse von SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)  
  
  
