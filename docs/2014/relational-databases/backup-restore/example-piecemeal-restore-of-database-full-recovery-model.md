---
title: 'Beispiel: Schrittweise Wiederherstellung einer Datenbank (vollständiges Wiederherstellungsmodell) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- piecemeal restores [SQL Server], full recovery model
- restore sequences [SQL Server], piecemeal
ms.assetid: 0a84892d-2f7a-4e77-b2d0-d68b95595210
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 157541fe3792ba082d9b1ec84c3ab45ca0617060
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62875822"
---
# <a name="example-piecemeal-restore-of-database-full-recovery-model"></a>Beispiel: Schrittweise Wiederherstellung einer Datenbank (vollständiges Wiederherstellungsmodell)
  Bei einer schrittweisen Wiederherstellungssequenz wird die Datenbank auf Dateigruppenebene stufenweise wiederhergestellt, wobei mit den primären Dateigruppen sowie mit den sekundären Dateigruppen mit Lese- und Schreibberechtigung begonnen wird.  
  
 In diesem Beispiel wird die `adb` -Datenbank nach einem Notfall auf einem neuen Computer wiederhergestellt. Für die Datenbank wird das vollständige Wiederherstellungsmodell verwendet, weshalb vor dem Beginn der Wiederherstellung eine Protokollfragmentsicherung der Datenbank erstellt werden muss. Vor dem Notfall sind alle Dateigruppen online. Dateigruppe `B` ist schreibgeschützt. Alle sekundären Dateigruppen müssen wiederhergestellt werden, aber sie werden in der Reihenfolge ihrer Wichtigkeit wiederhergestellt: `A` (höchste Wichtigkeit), `C`und schließlich `B`. In diesem Beispiel gibt es vier Protokollsicherungen, darunter die Protokollfragmentsicherung.  
  
## <a name="tail-log-backup"></a>Sicherung des Protokollfragments  
 Vor dem Wiederherstellen der Datenbank muss der Datenbankadministrator das Protokollfragment sichern. Weil die Datenbank beschädigt ist, muss zum Erstellen der Sicherung des Protokollfragments die NO_TRUNCATE-Option verwendet werden:  
  
```  
BACKUP LOG adb TO tailLogBackup WITH NORECOVERY, NO_TRUNCATE  
```  
  
 Bei der Sicherung des Protokollfragments handelt es sich um die letzte Sicherung im Rahmen der folgenden Wiederherstellungssequenzen.  
  
## <a name="restore-sequences"></a>Wiederherstellen von Sequenzen  
  
> [!NOTE]  
>  Die Syntax für eine Onlinewiederherstellungssequenz ist dieselbe wie bei einer Offlinewiederherstellungssequenz.  
  
1.  Teilweise Wiederherstellung der primären und sekundären Dateigruppe `A`.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
       WITH PARTIAL, NORECOVERY  
    RESTORE DATABASE adb FILEGROUP='A' FROM backup2   
       WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
2.  Onlinewiederherstellung der Dateigruppe `C`.  
  
     Jetzt sind die primäre Dateigruppe und die sekundäre Dateigruppe `A` online verfügbar. Für die Dateien in den Dateigruppen `B` und `C` steht die Wiederherstellung noch aus, d. h., die Dateigruppen sind noch offline.  
  
     In Meldungen aus der letzten `RESTORE LOG` -Anweisung (in Schritt 1) wird darauf hingewiesen, dass Rollbacks für Transaktionen mit Dateigruppe `C` verzögert werden, da die Dateigruppe nicht verfügbar ist. Normale Vorgänge können zwar fortgesetzt werden, allerdings werden durch die Transaktionen Sperren eingerichtet, und Protokollkürzungen sind erst nach Abschluss des Rollbacks möglich.  
  
     In der zweiten Wiederherstellungssequenz stellt der Administrator die Dateigruppe `C`wieder her:  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' FROM backup2a WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     Die primäre Dateigruppe und die Dateigruppen `A` und `C` sind zu diesem Zeitpunkt online. Für die Dateien in der Dateigruppe `B` steht weiterhin die Wiederherstellung aus; die Dateigruppe ist offline. Die verzögerten Transaktionen wurden aufgelöst, und die Protokollkürzungen werden vorgenommen.  
  
3.  Onlinewiederherstellung der Dateigruppe `B`.  
  
     In der dritten Wiederherstellungssequenz stellt der Administrator die Dateigruppe `B`wieder her: Die Sicherung von Dateigruppe `B` wurde erstellt, nachdem die Dateigruppe schreibgeschützt wurde. Deshalb muss für diese Dateien bei der Wiederherstellung kein Rollforward ausgeführt werden.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup2b WITH RECOVERY  
    ```  
  
     Alle Dateigruppen sind nun online.  
  
## <a name="additional-examples"></a>Zusätzliche Beispiele  
  
-   [Beispiel: Schrittweise Wiederherstellung einer Datenbank &#40;einfaches Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen &#40;einfaches Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;einfaches Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen &#40;vollständiges Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer Datei mit Lese-/Schreibzugriff &#40;vollständiges Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;vollständiges Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Onlinewiederherstellungen &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
