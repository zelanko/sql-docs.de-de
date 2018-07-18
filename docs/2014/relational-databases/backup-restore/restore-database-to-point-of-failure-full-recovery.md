---
title: Wiederherstellen einer Datenbank bis zum Zeitpunkt des Fehlers unter dem vollständigen Wiederherstellungsmodell (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- point of failure [SQL Server]
- restoring databases [SQL Server], point of failure
- database restores [SQL Server], point of failure
ms.assetid: 04106e18-bbf7-4a5e-a2e1-3d65319814d5
caps.latest.revision: 35
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ad1916a80b7e209773eacbafa4ec390e63be880b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271576"
---
# <a name="restore-a-database-to-the-point-of-failure-under-the-full-recovery-model-transact-sql"></a>Wiederherstellen einer Datenbank bis zum Fehlerzeitpunkt im vollständigen Wiederherstellungsmodell (Transact-SQL)
  In diesem Thema wird erläutert, wie Sie den Status vor dem Fehler wiederherstellen. Dieses Thema ist nur für Datenbanken relevant, von denen das vollständige oder massenprotokollierte Wiederherstellungsmodell verwendet wird.  
  
### <a name="to-restore-to-the-point-of-failure"></a>So stellen Sie den Status vor dem Fehler wieder her  
  
1.  Sichern Sie das Protokollfragment, indem Sie die folgende einfache [BACKUP](/sql/t-sql/statements/backup-transact-sql) -Anweisung ausführen:  
  
    ```  
    BACKUP LOG <database_name> TO <backup_device>   
       WITH NORECOVERY, NO_TRUNCATE;  
    ```  
  
2.  Stellen Sie eine vollständige Datenbanksicherung wieder her, indem Sie folgende einfache [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) -Anweisung ausführen:  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
3.  Stellen Sie optional eine differenzielle Datenbanksicherung wieder her, indem Sie folgende einfache RESTORE DATABASE-Anweisung ausführen:  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
4.  Wenden Sie jedes Transaktionsprotokoll an, einschließlich der von Ihnen in Schritt 1 erstellten Sicherung des Protokollfragments. Geben Sie dazu WITH NORECOVERY in der RESTORE LOG-Anweisung an.  
  
    ```  
    RESTORE LOG <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
5.  Stellen Sie die Datenbank wieder her, indem Sie folgende RESTORE DATABASE-Anweisung ausführen:  
  
    ```  
    RESTORE DATABASE <database_name>   
       WITH RECOVERY;  
    ```  
  
## <a name="example"></a>Beispiel  
 Bevor Sie das Beispiel ausführen können, sind folgende Vorbereitungen erforderlich:  
  
1.  Das Standardwiederherstellungsmodell der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank ist das einfache Wiederherstellungsmodell. Da dieses Wiederherstellungsmodell nicht die Wiederherstellung bis zum Zeitpunkt des Fehlers unterstützt, müssen Sie für [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] die Verwendung des vollständigen Wiederherstellungsmodells festlegen, indem Sie folgende [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) -Anweisung ausführen:  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
    ```  
  
2.  Erstellen Sie eine vollständige Datenbanksicherung der Datenbank, indem Sie folgende BACKUP-Anweisung verwenden:  
  
    ```  
    BACKUP DATABASE AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Data.bck';  
    ```  
  
3.  Erstellen Sie eine routinemäßige Protokollsicherung:  
  
    ```  
    BACKUP LOG AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Log.bck';  
    ```  
  
 Im folgenden Beispiel werden die zuvor erstellten Sicherungen wiederhergestellt, nachdem eine Protokollfragmentsicherung der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank erstellt wird. (Für diesen Schritt wird vorausgesetzt, dass der Zugriff auf den Protokolldatenträger möglich ist.)  
  
 Zunächst wird im Beispiel eine Protokollfragmentsicherung der Datenbank erstellt, wobei das aktive Protokoll erfasst und die Datenbank im Wiederherstellungszustand belassen wird. Dann wird im Beispiel die Datenbanksicherung wiederhergestellt, die zuvor erstellte routinemäßige Protokollsicherung angewendet und die Protokollfragmentsicherung angewendet. Abschließend wird die Datenbank in einem separaten Schritt wiederhergestellt.  
  
> [!NOTE]  
>  Das Standardverhalten besteht in der Wiederherstellung einer Datenbank als Bestandteil der Anweisung, mit der die endgültige Sicherung wiederhergestellt wird.  
  
```  
/* Example of restoring a to the point of failure */  
-- Step 1: Create a tail-log backup by using WITH NORECOVERY.  
BACKUP LOG AdventureWorks2012  
   TO DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 2: Restore the full database backup.  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Data.bck'  
   WITH NORECOVERY;  
GO  
-- Step 3: Restore the first transaction log backup.  
RESTORE LOG AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 4: Restore the tail-log backup.  
RESTORE LOG AdventureWorks2012  
   FROM  DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 5: Recover the database.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
