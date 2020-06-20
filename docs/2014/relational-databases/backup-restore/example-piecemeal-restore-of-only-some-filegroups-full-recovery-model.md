---
title: 'Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen (Vollständiges Wiederherstellungsmodell) | Microsoft-Dokumentation'
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
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b3cb1a5ea33a5016c99fdf1f5a7f4e892c045b59
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84958146"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-full-recovery-model"></a>Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen (Vollständiges Wiederherstellungsmodell)
  Dieses Thema ist nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken mit mehreren Dateien oder Dateigruppen im vollständigen Wiederherstellungsmodell relevant.  
  
 Mit einer schrittweisen Wiederherstellungssequenz wird eine Datenbank phasenweise auf Dateigruppenebene wiederhergestellt, beginnend mit der primären Dateigruppe und allen sekundären Dateigruppen mit Lese-/Schreibzugriff.  
  
 In diesem Beispiel enthält die Datenbank `adb`, für die das vollständige Wiederherstellungsmodell verwendet wird, drei Dateigruppen. Die Dateigruppe `A` weist Lese-/Schreibzugriff auf, die Dateigruppen `B` und `C` sind schreibgeschützt. Zu Beginn sind alle Dateigruppen online.  
  
 Die primäre Dateigruppe und die Dateigruppe `B` der `adb` -Datenbank scheinen beschädigt zu sein. Die primäre Dateigruppe ist ziemlich klein und kann schnell wiederhergestellt werden. Der Datenbankadministrator beschließt, sie mithilfe einer schrittweisen Wiederherstellungssequenz wiederherzustellen. Zunächst werden die primäre Dateigruppe und die nachfolgenden Transaktionsprotokolle wiederhergestellt.  
  
 In den intakten Dateigruppen `A` und `C` sind wichtige Daten enthalten. Deshalb werden sie anschließend wiederhergestellt, um sie so schnell wie möglich online zu schalten. Schließlich wird die beschädigte sekundäre Dateigruppe `B`wiederhergestellt.  
  
## <a name="restore-sequences"></a>Wiederherstellungssequenzen  
  
> [!NOTE]  
>  Die Syntax für eine Onlinewiederherstellungssequenz ist dieselbe wie bei einer Offlinewiederherstellungssequenz.  
  
1.  Erstellen Sie eine Sicherung des Protokollfragments der `adb`-Datenbank. Dieser Schritt ist entscheidend dafür, dass die intakten Dateigruppen `A` und `C` mit dem Wiederherstellungspunkt der Datenbank übereinstimmen.  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  Teilweise Wiederherstellung der primären Dateigruppe.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     Die primäre Dateigruppe ist zu diesem Zeitpunkt online. Für Dateien in den Dateigruppen `A`, `B`und `C` steht die Wiederherstellung aus, und die Dateigruppen sind offline.  
  
3.  Onlinewiederherstellung der Dateigruppen `A` und `C`.  
  
     Da die Daten unbeschädigt sind, müssen diese Dateigruppen nicht anhand einer Sicherung wiederhergestellt werden. Sie müssen jedoch wiederhergestellt werden, damit sie online geschaltet werden können.  
  
     Der Datenbankadministrator stellt `A` und `C` sofort wieder her.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     Die primäre Dateigruppe und die Dateigruppen `A` und `C` sind zu diesem Zeitpunkt online. Für die Dateien in der Dateigruppe `B` steht weiterhin die Wiederherstellung aus; die Dateigruppe ist offline.  
  
4.  Onlinewiederherstellung der Dateigruppe `B`.  
  
     Die Dateien in der Dateigruppe `B` werden zu einem beliebigen späteren Zeitpunkt wiederhergestellt.  
  
    > [!NOTE]  
    >  Die Sicherung von Dateigruppe `B` wurde erstellt, nachdem die Dateigruppe als schreibgeschützt gekennzeichnet wurde. Deshalb muss für diese Dateien kein Rollforward ausgeführt werden.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     Alle Dateigruppen sind nun online.  
  
## <a name="additional-examples"></a>Zusätzliche Beispiele  
  
-   [Beispiel: Schrittweise Wiederherstellung einer Datenbank &#40;Einfaches Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen &#40;einfaches Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;einfaches Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung einer Datenbank &#40;Vollständiges Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer Datei mit Lese-/Schreibzugriff &#40;vollständiges Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;vollständiges Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Onlinewiederherstellungen &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
