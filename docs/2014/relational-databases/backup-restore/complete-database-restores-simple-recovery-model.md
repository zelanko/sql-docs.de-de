---
title: Vollständige Datenbankwiederherstellungen (einfaches Wiederherstellungsmodell) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- simple recovery model [SQL Server]
- restoring [SQL Server], database
ms.assetid: 49828927-1727-4d1d-9ef5-3de43f68c026
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e64bf4d4642d8091cd0892283a996e7dccc56e26
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877150"
---
# <a name="complete-database-restores-simple-recovery-model"></a>Vollständige Datenbankwiederherstellungen (einfaches Wiederherstellungsmodell)
  Das Ziel einer vollständigen Datenbankwiederherstellung besteht in der Wiederherstellung der gesamten Datenbank. Die gesamte Datenbank ist für die Dauer der Wiederherstellung offline. Bevor Teile der Datenbank wieder online zur Verfügung gestellt werden können, müssen alle Daten bis zu einem konsistenten Zeitpunkt wiederhergestellt werden. Ein solcher Punkt ist gegeben, wenn für alle Teile der Datenbank derselbe Zeitpunkt gilt und keine Transaktionen ohne Commit vorhanden sind.  
  
 Im einfachen Wiederherstellungsmodell kann die Datenbank nicht bis zu einem bestimmten Zeitpunkt innerhalb eines bestimmten Sicherungsvorgangs wiederhergestellt werden.  
  
> [!IMPORTANT]  
>  Das Anfügen oder Wiederherstellen von Datenbanken aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Diese Datenbanken können bösartigen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Code ausführt oder Fehler durch Ändern des Schemas oder der physischen Datenbankstruktur erzeugt. Bevor Sie eine Datenbank aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, führen Sie auf einem Nichtproduktionsserver [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) für die Datenbank aus. Überprüfen Sie außerdem den Code in der Datenbank, z.B. gespeicherte Prozeduren oder anderen benutzerdefinierten Code.  
  

  
> [!NOTE]  
>  Informationen zur Unterstützung von Sicherungskopien früherer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Versionen finden Sie im Kapitel [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)im Abschnitt „Kompatibilitätsunterstützung“.  
  
##  <a name="Overview"></a> Übersicht über die Datenbankwiederherstellung mit dem einfachen Wiederherstellungsmodell  
 Für eine vollständige Datenbankwiederherstellung mit dem einfachen Wiederherstellungsmodell sind nur ein oder zwei [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) -Anweisungen erforderlich, je nachdem, ob Sie eine differenzielle Datenbanksicherung wiederherstellen möchten. Stellen Sie lediglich die letzte Sicherung wieder her, wie in der folgenden Abbildung dargestellt, wenn Sie nur eine vollständige Datenbanksicherung verwenden:  
  
 ![Wiederherstellung nur einer vollständigen Datenbanksicherung](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "Restoring only a full database backup")  
  
 Wenn Sie auch eine differenzielle Datenbanksicherung verwenden, stellen Sie die letzte vollständige Datenbanksicherung wieder her, ohne die Datenbank wiederherzustellen. Anschließend stellen Sie die letzte differenzielle Datenbanksicherung wieder her und stellen die Datenbank wieder her. Die folgende Abbildung veranschaulicht diesen Prozess:  
  
 ![Wiederherstellung von vollständigen und von differenziellen Datenbanksicherungen](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "Restoring full and differential database backups")  
  
> [!NOTE]  
>  Informationen zum Wiederherstellen einer Datenbanksicherung auf einer anderen Serverinstanz finden Sie unter [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../databases/copy-databases-with-backup-and-restore.md).  
  
###  <a name="TsqlSyntax"></a> Grundlegende Transact-SQL-RESTORE-Syntax  
 Die grundlegende [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) -Syntax zur Wiederherstellung einer vollständigen Datenbanksicherung lautet:  
  
 RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]  
  
> [!NOTE]  
>  Verwenden Sie WITH NORECOVERY, wenn Sie planen, auch eine differenzielle Datenbanksicherung wiederherzustellen.  
  
 Die grundlegende [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) -Syntax zur Wiederherstellung einer Datenbanksicherung lautet:  
  
 RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY  
  
###  <a name="Example"></a> Beispiel (Transact-SQL)  
 Das folgende Beispiel zeigt zunächst, wie die [BACKUP](/sql/t-sql/statements/backup-transact-sql) -Anweisung zum Erstellen einer vollständigen Datenbanksicherung und einer differenziellen Datenbanksicherung der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank verwendet wird. Anschließend werden diese Sicherungen im Beispiel nacheinander wiederhergestellt. Die Datenbank wird zu dem Status wiederhergestellt, in dem sie sich beim Abschließen der differenziellen Datenbanksicherung befand.  
  
 Im Beispiel werden die wichtigen Optionen in einer Wiederherstellungssequenz für das Szenario der vollständigen Datenbankwiederherstellung veranschaulicht. Eine *Wiederherstellungssequenz* besteht aus mindestens einem Wiederherstellungsvorgang, mit dessen Hilfe Daten mindestens eine Wiederherstellungsphase durchlaufen. Hierfür unwichtige Syntax und Informationen werden ausgelassen. Wenn Sie eine Datenbank wiederherstellen, wird empfohlen, die Option RECOVERY aus Gründen der Klarheit explizit anzugeben, obwohl das die Standardvorgabe ist.  
  
> [!NOTE]  
>  Das Beispiel beginnt mit einer [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) -Anweisung, mit der das Wiederherstellungsmodell auf `SIMPLE`festgelegt wird.  
  
```  
USE master;  
--Make sure the database is using the simple recovery model.  
ALTER DATABASE AdventureWorks2012 SET RECOVERY SIMPLE;  
GO  
-- Back up the full AdventureWorks2012 database.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
  WITH FORMAT;  
GO  
--Create a differential database backup.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH DIFFERENTIAL;  
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=1, NORECOVERY;  
--Restore the differential backup (from backup set 2).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=2, RECOVERY;  
GO  
```  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So stellen Sie eine vollständige Datenbanksicherung wieder her**  
  
-   [Wiederherstellen einer Datenbanksicherung unter dem einfachen Wiederherstellungsmodell &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)  
  
 **So stellen Sie eine differenzielle Datenbanksicherung wieder her**  
  
-   [Wiederherstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md)  
  
 **So stellen Sie eine Sicherung mithilfe von SQL Server Management Objects (SMO) wieder her**  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  

  
## <a name="see-also"></a>Siehe auch  
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [Vollständige Datenbanksicherungen &#40;SQL Server&#41;](full-database-backups-sql-server.md)   
 [Differenzielle Sicherungen &#40;SQL Server&#41;](differential-backups-sql-server.md)   
 [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Übersicht über Wiederherstellungsvorgänge &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)  
  
  
