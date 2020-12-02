---
title: Dateiwiederherstellungen (einfaches Wiederherstellungsmodell) | Microsoft-Dokumentation
description: In SQL Server wird eine Dateiwiederherstellung für eine oder mehrere beschädigte Dateien durchgeführt, ohne dass dabei die gesamte Datenbank wiederhergestellt wird.
ms.custom: ''
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- simple recovery model [SQL Server]
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- Transact-SQL restore sequence
- restoring files [SQL Server], simple recovery model
- file restores [SQL Server], simple recovery model
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
author: cawrites
ms.author: chadam
ms.openlocfilehash: 7722c033fd9434f04c70b046aeaa91591f30dd3c
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "96126935"
---
# <a name="file-restores-simple-recovery-model"></a>Dateiwiederherstellungen (einfaches Wiederherstellungsmodell)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Dieses Thema betrifft nur Datenbanken, die auf dem einfachen Wiederherstellungsmodell basieren und mindestens eine schreibgeschützte sekundäre Dateigruppe enthalten.  
  
 Das Ziel einer Dateiwiederherstellung besteht darin, eine oder mehrere beschädigte Dateien wiederherzustellen, ohne dabei die gesamte Datenbank wiederherstellen zu müssen. Beim einfachen Wiederherstellungsmodell werden Dateisicherungen nur für schreibgeschützte Dateien unterstützt. Die primäre Dateigruppe und die sekundären Dateigruppen mit Lese-/Schreibzugriff werden immer zusammen wiederhergestellt (durch Wiederherstellen einer Datenbank- oder Teilsicherung).  
  
 Für die Dateiwiederherstellung sind folgende Szenarien möglich:  
  
-   Offlinedateiwiederherstellung  
  
     Bei einer *Offlinedateiwiederherstellung* ist die Datenbank offline, während die beschädigten Dateien oder Dateigruppen wiederhergestellt werden. Am Ende der Wiederherstellungssequenz wird die Datenbank wieder online geschaltet.  
  
     Offlinewiederherstellungen werden von allen Editionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unterstützt.  
  
-   Onlinedateiwiederherstellung  
  
     Bei einer *Onlinedateiwiederherstellung* bleibt die Datenbank online, wenn die Datenbank während einer Dateiwiederherstellung online ist. Dateigruppen, in denen eine Datei wiederhergestellt wird, sind während des Wiederherstellungsvorgangs jedoch offline. Sobald die Dateien einer Offlinedateigruppe wiederhergestellt sind, wird die Dateigruppe automatisch wieder online geschaltet.  
  
     Informationen zur Unterstützung für Seiten- und Dateiwiederherstellung im Onlinemodus finden Sie unter [Datenbank-Engine-Funktionen und Tasks](../../sql-server/what-s-new-in-sql-server-ver15.md). Weitere Informationen zur Onlinewiederherstellung finden Sie unter [Onlinewiederherstellung &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md).  
  
    > [!TIP]  
    >  Wenn Sie möchten, dass die Datenbank für eine Dateiwiederherstellung offline ist, können Sie die Datenbank vor dem Starten der Wiederherstellungssequenz offline schalten, indem Sie die folgende [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-set-options.md)-Anweisung ausführen: ALTER DATABASE *Datenbankname* SET OFFLINE  
  
 **In diesem Thema:**  
  
-   [Übersicht über Datei- und Dateigruppenwiederherstellung mit dem einfachen Wiederherstellungsmodell](#Overview)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="overview-of-file-and-filegroup-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> Übersicht über Datei- und Dateigruppenwiederherstellung mit dem einfachen Wiederherstellungsmodell  
 Ein Dateiwiederherstellungsszenario besteht aus einer einzelnen Wiederherstellungssequenz, bei der die geeigneten Daten kopiert, ein Rollforward ausgeführt und die Daten anschließend wiederhergestellt werden:  
  
1.  Jede beschädigte Datei wird von der letzten Dateisicherung wiederhergestellt.  
  
2.  Für jede wiederhergestellte Datei wird die letzte differenzielle Dateisicherung und dann die Datenbank wiederhergestellt.  
  
### <a name="transact-sql-steps-for-file-restore-sequence-simple-recovery-model"></a>Transact-SQL-Schritte für die Dateiwiederherstellungssequenz (einfaches Wiederherstellungsmodell)  
 In diesem Abschnitt werden die grundlegenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-[RESTORE](../../t-sql/statements/restore-statements-transact-sql.md)-Optionen für eine einfache Dateiwiederherstellungssequenz erläutert. Hierfür unwichtige Syntax und Informationen werden ausgelassen.  
  
 Die Wiederherstellungssequenz enthält nur zwei [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen. Mit der ersten Anweisung wird unter Verwendung von WITH NORECOVERY eine sekundäre Datei (Datei `A`) wiederhergestellt. Im zweiten Vorgang werden unter Verwendung von WITH RECOVERY zwei weitere Dateien ( `B` und `C` ) von einem anderen Sicherungsmedium wiederhergestellt:  
  
1.  RESTORE DATABASE *Datenbank* FILE **=** _Name_von_Datei_A_  
  
     FROM *Dateisicherung_von_Datei_A*  
  
     WITH NORECOVERY **;**  
  
2.  RESTORE DATABASE *Datenbank* FILE **=** _Name_von_Datei_B_ **,** _Name_von_Datei_C_  
  
     FROM *Dateisicherung_der_Dateien_B_und_C*  
  
     WITH RECOVERY **;**  
  
### <a name="examples"></a>Beispiele  
  
-   [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;einfaches Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Beispiel: Offlinewiederherstellung der primären Dateigruppe und einer weiteren Dateigruppe &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So stellen Sie Dateien und Dateigruppen wieder her**  
  
-   [Wiederherstellen von Dateien und Dateigruppen über vorhandene Dateien &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [Wiederherstellen von Dateien und Dateigruppen &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [Wiederherstellen von Dateien und Dateigruppen &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [Restore.SqlRestore-Methode (Server) (SMO)](/dotnet/api/microsoft.sqlserver.management.smo.restore.sqlrestore)   
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherung und Wiederherstellung: Interoperabilität und gleichzeitige Verwendung &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-and-restore-interoperability-and-coexistence-sql-server.md)   
 [Differenzielle Sicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md)   
 [Vollständige Dateisicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-file-backups-sql-server.md)   
 [Übersicht über Sicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [Übersicht über Wiederherstellungsvorgänge &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
