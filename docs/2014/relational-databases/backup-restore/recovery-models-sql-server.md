---
title: Wiederherstellungsmodelle (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], recovery models
- bulk-logged recovery model [SQL Server]
- recovery [SQL Server], recovery model
- restoring transaction logs [SQL Server], recovery models
- backing up databases [SQL Server], recovery models
- recovery models [SQL Server], about
- transaction log backups [SQL Server]
- simple recovery model [SQL Server]
- backups [SQL Server], recovery models
- recovery models [SQL Server]
- recovery models [SQL Server], transaction log management
- database restores [SQL Server], recovery models
- transaction log restores [SQL Server]
- logs [SQL Server], recovery models
- restoring databases [SQL Server], recovery models
- full recovery model [SQL Server]
- backing up transaction logs [SQL Server], recovery models
ms.assetid: 8cfea566-8f89-4581-b30d-c53f1f2c79eb
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6c5b85e316c859e0b6d44fb83e3df6da2edd72ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62921765"
---
# <a name="recovery-models-sql-server"></a>Wiederherstellungsmodelle (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungs- und Wiederherstellungsvorgänge werden im Kontext des Wiederherstellungsmodells der Datenbank durchgeführt. Mit Wiederherstellungsmodellen wird die Wartung des Transaktionsprotokolls gesteuert. Ein *Wiederherstellungsmodell* ist eine Datenbankeigenschaft, die steuert, wie Transaktionen protokolliert werden, ob das Transaktionsprotokoll gesichert werden muss (und kann) und welche Arten von Wiederherstellungsvorgängen verfügbar sind. Es stehen drei Wiederherstellungsmodelle zur Verfügung: einfach, vollständig und massenprotokolliert. Für eine Datenbank wird im Allgemeinen das vollständige oder das einfache Wiederherstellungsmodell verwendet. Eine Datenbank kann jederzeit auf ein anderes Wiederherstellungsmodell umgestellt werden.  
  
 **In diesem Thema:**  
  
-   [Übersicht über Wiederherstellungsmodelle](#RMov)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="RMov"></a> Übersicht über Wiederherstellungsmodelle  
 Die folgende Tabelle enthält eine Zusammenfassung der drei Wiederherstellungsmodelle:  
  
|Wiederherstellungsmodell|BESCHREIBUNG|Datenverlust|Wiederherstellung bis zu einem bestimmten Zeitpunkt?|  
|--------------------|-----------------|------------------------|-------------------------------|  
|**Einfach**|Keine Protokollsicherungen.<br /><br /> Gibt Protokollspeicherplatz automatisch wieder frei, um die Speicherplatzanforderungen gering zu halten. Hierdurch entfällt im Wesentlichen die Notwendigkeit, den Speicherplatz für Transaktionsprotokolle zu verwalten. Informationen zu Datenbanksicherungen unter dem einfachen Wiederherstellungsmodell finden Sie unter [Vollständige Datenbanksicherungen &#40;SQL Server&#41;](full-database-backups-sql-server.md).<br /><br /> Vorgänge, die Transaktionsprotokollsicherungen erfordern, werden vom einfachen Wiederherstellungsmodell nicht unterstützt. Die folgenden Funktionen können beim einfachen Wiederherstellungsmodus verwendet werden:<br /><br /> Protokollversand<br /><br /> AlwaysOn oder Datenbankspiegelung<br /><br /> Medienwiederherstellung ohne Datenverlust<br /><br /> Wiederherstellungen bis zu einem bestimmten Zeitpunkt|Änderungen seit der letzten Sicherung sind nicht geschützt. Bei Auftreten eines Notfalls müssen diese Änderungen erneut vorgenommen werden.|Die Wiederherstellung ist nur bis zum Ende einer Sicherung möglich. Weitere Informationen finden Sie unter [Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](complete-database-restores-simple-recovery-model.md).|  
|**Vollständig**|Erfordert Protokollsicherungen.<br /><br /> Es gehen keine Daten aufgrund einer verlorenen oder beschädigten Datendatei verloren.<br /><br /> Die Wiederherstellung bis zu einem beliebigen Zeitpunkt ist möglich (z. B. vor Anwendungs- oder Benutzerfehlern). Informationen zu Datenbanksicherungen unter dem vollständigen Wiederherstellungsmodell finden Sie unter [Vollständige Datenbanksicherungen &#40;SQL Server&#41;](full-database-backups-sql-server.md) und [Vollständige Datenbankwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](complete-database-restores-full-recovery-model.md).|Normalerweise nicht.<br /><br /> Wenn das Protokollfragment beschädigt ist, müssen Änderungen seit der letzten Protokollsicherung erneut vorgenommen werden.|Die Wiederherstellung bis zu einem bestimmten Zeitpunkt ist möglich, vorausgesetzt die Sicherungen sind bis zu diesem Zeitpunkt vollständig. Informationen zur Verwendung von Protokollsicherungen, um bis zum Punkt des Fehlers wiederherzustellen, finden Sie unter [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).<br /><br /> Hinweis: Bei mindestens zwei Datenbanken mit vollständigem Wiederherstellungsmodell, die logisch konsistent sein sollen, müssen Sie möglicherweise eine spezielle Vorgehensweise implementieren, um die Wiederherstellbarkeit dieser Datenbanken sicherzustellen. Weitere Informationen finden Sie unter [Wiederherstellen verwandter Datenbanken mit einer markierten Transaktion](recovery-of-related-databases-that-contain-marked-transaction.md).|  
|**Massenprotokolliert**|Erfordert Protokollsicherungen.<br /><br /> Eine Ergänzung des vollständigen Wiederherstellungsmodells, die leistungsintensive Massenkopiervorgänge ermöglicht.<br /><br /> Senkt die Protokollspeicherauslastung durch den Einsatz von minimaler Protokollierung für die meisten Massenvorgänge. Informationen zu Vorgängen, die minimal protokolliert werden können, finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).<br /><br /> Informationen zu Datenbanksicherungen unter dem massenprotokollierten Wiederherstellungsmodell finden Sie unter [Vollständige Datenbanksicherungen &#40;SQL Server&#41;](full-database-backups-sql-server.md) und [Vollständige Datenbankwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](complete-database-restores-full-recovery-model.md).|Wenn das Protokoll beschädigt ist oder massenprotokollierte Vorgänge seit der letzten Protokollsicherung aufgetreten sind, müssen Änderungen seit der letzten Protokollsicherung erneut vorgenommen werden.<br /><br /> Ansonsten gehen keine Daten verloren.|Die Wiederherstellung bis zum Ende einer beliebigen Sicherung ist möglich. Die Zeitpunktwiederherstellung wird nicht unterstützt.|  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  
-   [Problembehandlung bei vollen Transaktionsprotokollen &#40;SQL Server-Fehler 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)   
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](back-up-and-restore-of-sql-server-databases.md)   
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)   
 [Automatisierte Administrationstasks &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md)   
 [Übersicht über Wiederherstellungsvorgänge &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)  
  
  
