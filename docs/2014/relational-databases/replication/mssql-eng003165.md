---
title: MSSQL_ENG003165 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003165 error
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c4c2c6e01fd3e0b862511f71d90baf31d28948ef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666706"
---
# <a name="mssqleng003165"></a>MSSQL_ENG003165
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3165|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Die %1!s!-Datenbank wurde wiederhergestellt; beim Wiederherstellen/Entfernen der Replikation wurde jedoch ein Fehler erkannt. Die Datenbank ist offline. Weitere Informationen finden Sie im Thema 'MSSQL_ENG003165' in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler wird ausgelöst, wenn beim Wiederherstellen einer Sicherung für eine replizierte Datenbank ein Problem auftritt.  
  
-   Wenn die Sicherung in dieselbe Datenbank und auf denselben Server wiederhergestellt wird, woher sie stammt, bedeutet der Fehler, dass die Replikationseinstellungen nicht ordnungsgemäß wiederhergestellt werden konnten.  
  
-   Wenn die Sicherung in eine andere Datenbank oder auf einen anderen Server wiederhergestellt wird, bedeutet der Fehler, dass die Repliktionseinstellungen nicht ordnungsgemäß entfernt werden konnten (die Replikationseinstellungen werden bei einer anderen Datenbank oder einem anderen Server standardmäßig entfernt).  
  
 Der Fehler ist vermutlich das Ergebnis einer fehlenden Übereinstimmung zwischen dem Status der wiederhergestellten Datenbank und einer oder mehreren Systemdatenbanken, die Replikationsmetadaten enthalten: **msdb**, **master**oder der Verteilungsdatenbank.  
  
## <a name="user-action"></a>Benutzeraktion  
 So lösen Sie das Problem:  
  
1.  Führen Sie ALTER DATABASE aus, um die Datenbank offline zu schalten; Beispiel: `ALTER DATABASE AdventureWorks SET ONLINE`. Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql). Wenn Sie die Replikationseinstellungen beibehalten möchten, fahren Sie mit Schritt 2 fort. Andernfalls fahren Sie mit Schritt 3 fort.  
  
2.  Führen Sie [sp_restoredbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql) aus. Wenn diese gespeicherte Prozedur erfolgreich ausgeführt wird, ist die Wiederherstellung abgeschlossen. Falls die Ausführung nicht erfolgreich verlief, fahren Sie mit Schritt 3 fort.  
  
3.  Führen Sie [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) aus, um alle Replikationseinstellungen zu entfernen.  
  
     Konfigurieren Sie gegebenenfalls die Replikation neu. Wenn Sie wie empfohlen Skripts für die Replikationstopologie erstellt haben, verwenden Sie Skripts, um die Topologie neu zu konfigurieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Sichern und Wiederherstellen von replizierten Datenbanken](administration/back-up-and-restore-replicated-databases.md)   
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
