---
title: MSSQLSERVER_8651 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a28655b2f86c02b1985196c05c16b866e3e0897
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637130"
---
# <a name="mssqlserver_8651"></a>MSSQLSERVER_8651
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|8651|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|MEMGRANT_ERR|  
|Meldungstext|Der angeforderte Vorgang konnte nicht ausgeführt werden, da das benötigte Minimum an Arbeitsspeicher für die Abfrage nicht verfügbar ist. Verwenden Sie einen niedrigeren Wert für die Serverkonfigurationsoption 'Min. Arbeitsspeicher pro Abfrage'.|  
  
## <a name="explanation"></a>Erklärung  
Andere Prozesse verbrauchen Serverarbeitsspeicher (Arbeitsspeicherknappheit im Server).  
  
## <a name="user-action"></a>Benutzeraktion  
Entweder muss der konfigurierte Wert für die Serverkonfigurationsoption 'Min. Arbeitsspeicher pro Abfrage' verringert werden, oder die Abfrageauslastung auf dem Server muss reduziert werden.  
  
In der folgenden Liste werden allgemeine Schritte erläutert, die bei der Problembehandlung von Arbeitsspeicherfehlern helfen:  
  
1.  Überprüfen Sie, ob andere Anwendungen oder Dienste Arbeitsspeicher auf dem Server beanspruchen. Rekonfigurieren Sie weniger kritische Anwendungen oder Dienste, damit sie weniger Speicher beanspruchen.  
  
2.  Beginnen Sie mit der Erfassung von Leistungsüberwachungsindikatoren für **SQL Server: Puffer-Manager**, **SQL Server: Speicher-Manager**.  
  
3.  Überprüfen Sie die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicherkonfigurationsparameter:  
  
    -   **Max. Serverarbeitsspeicher**  
  
    -   **Min. Serverarbeitsspeicher**  
  
    -   **Min. Arbeitsspeicher pro Abfrage**  
  
    Achten Sie auf ungewöhnliche Einstellungen. Berichtigen Sie sie bei Bedarf. Die Standardeinstellungen werden unter "Festlegen von Serverkonfigurationsoptionen" in der SQL Server-Onlinedokumentation aufgeführt.  
  
4.  Überprüfen Sie die Arbeitsauslastung (z. B. Anzahl gleichzeitiger Sitzungen, derzeit ausgeführte Abfragen).  

Durch die folgenden Aktionen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mehr Arbeitsspeicher zur Verfügung gestellt werden:  
  
-   Wenn andere Anwendungen als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ressourcen verbrauchen, versuchen Sie, diese Anwendungen zu beenden, oder führen Sie sie auf einem separaten Server aus. Dadurch fällt der Mangel an externem Arbeitsspeicher weg.  
  
-   Wenn Sie **Max. Serverarbeitsspeicher**  konfiguriert haben, erhöhen Sie dessen Wert.  
  
Führen Sie die folgenden DBCC-Befehle aus, um mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speichercaches freizugeben.  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Wenn das Problem weiterhin besteht, müssen Sie weitere Untersuchungen ausführen und möglicherweise die Arbeitsauslastung reduzieren.  
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC FREESYSTEMCACHE &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql.md)  
[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql.md)  
[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)  
[Serverkonfigurationsoptionen &#40;SQL Server&#41;](~/database-engine/configure-windows/server-configuration-options-sql-server.md)  
[SQL Server, Puffer-Manager-Objekt](~/relational-databases/performance-monitor/sql-server-buffer-manager-object.md)  
[SQL Server, Speicher-Manager-Objekt](~/relational-databases/performance-monitor/sql-server-memory-manager-object.md)  
  
