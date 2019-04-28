---
title: Wiederherstellen von Sicherungen in Windows Azure gespeicherten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6ae358b2-6f6f-46e0-a7c8-f9ac6ce79a0e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 549efcd796d9cef721995b48fc5e7b3cc02403a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920647"
---
# <a name="restoring-from-backups-stored-in-windows-azure"></a>Wiederherstellen von in Windows Azure gespeicherten Sicherungen
  In diesem Thema werden Überlegungen aufgeführt, die beim Wiederherstellen einer Datenbank aus einer Sicherung berücksichtigt werden müssen, die die im Windows Azure-BLOB-Speicherdienst gespeichert wurde. Dies gilt für Sicherungen, die mithilfe der SQL Server-Sicherung über URLs oder durch [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]erstellt wurden.  
  
 Eine Durchsicht dieses Themas wird empfohlen, wenn Sie im Windows Azure-BLOB-Speicherdienst gespeicherte Sicherungen wiederherstellen möchten. Lesen Sie anschließend die Themen, in denen die Schritte zum Wiederherstellen einer Datenbank beschrieben werden. Die Vorgehensweise ist für lokale und für Azure-Sicherungen identisch.  
  
## <a name="overview"></a>Übersicht  
 Die Tools und Methoden, die zum Wiederherstellen einer Datenbank aus einer lokalen Sicherung verwendet werden, sind ebenso für das Wiederherstellen einer Datenbank aus einer Cloud-Sicherung geeignet.  In den folgenden Abschnitten werden diese Überlegungen und die Unterschiede beschrieben, die sie beachten müssen, wenn Sie mit Sicherungen arbeiten, die in einem Windows Azure-BLOB-Speicherdienst gespeichert wurden.  
  
### <a name="using-transact-sql"></a>Verwenden von Transact-SQL  
  
-   Da SQL Server eine Verbindung mit einer externen Datenquelle herstellen muss, um die Sicherungsdateien abzurufen, werden SQL-Anmeldeinformationen für die Authentifizierung beim Speicherkonto verwendet. Aus diesem Grund muss die RESTORE-Anweisung mit der Option WITH CREDENTIAL angegeben werden. Weitere Informationen finden Sie unter [SQL Server-Sicherung und -Wiederherstellung mit dem Windows Azure-BLOB-Speicherdienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
-   Wenn Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Verwaltung von Sicherungen in der Cloud verwenden, können Sie mit der **smart_admin.fn_available_backups** -Systemfunktion alle im Speicher verfügbaren Sicherungen überprüfen. Diese Systemfunktion eine Tabelle mit allen verfügbaren Sicherungen für eine Datenbank zurück. Da die Ergebnisse in einer Tabelle zurückgegeben werden, können Sie die Ergebnisse filtern oder sortieren. Weitere Informationen finden Sie unter [fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql).  
  
### <a name="using-sql-server-management-studio"></a>Verwendung von SQL Server Management Studio  
  
-   Beim Verwenden von SQL Server Management Studio wird der Wiederherstellungstask zum Wiederherstellen einer Datenbank verwendet. Auf der Seite Sicherungsmedien ist jetzt auch die Option **URL** verfügbar, mit der Sicherungsdateien angezeigt werden können, die im Windows Azure-BLOB-Speicherdienst gespeichert sind. Sie müssen auch die SQL-Anmeldeinformationen angeben, die zur Authentifizierung beim Speicherkonto verwendet werden. Im Raster **Wiederherzustellende Sicherungssätze** werden daraufhin alle im Windows Azure-BLOB-Speicher verfügbaren Sicherungen angezeigt. Weitere Informationen finden Sie unter [wiederherstellen aus dem Windows Azure-Speicher mit SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS).  
  
### <a name="optimizing-restores"></a>Optimieren der Wiederherstellungsvorgänge  
 Um das Schreiben von Wiederherstellungsdaten zu beschleunigen, fügen Sie dem SQL Server-Benutzerkonto die Benutzerberechtigung **Durchführen von Volumewartungsaufgaben** hinzu. Weitere Informationen finden Sie unter [Datenbankdatei-Initialisierung](https://go.microsoft.com/fwlink/?LinkId=271622). Wenn die Wiederherstellung trotz aktivierter sofortiger Dateiinitialisierung noch langsam verläuft, sollten Sie die Größe der Protokolldatei auf der Instanz überprüfen, auf der die Datenbank gesichert wurde. Wenn das Protokoll sehr groß ist (mehrere GB umfasst), ist zu erwarten, dass die Wiederherstellung langsam verläuft. Während der Wiederherstellung muss die Protokolldatei mit Nullen (0) aufgefüllt werden, was beträchtliche Zeit in Anspruch nehmen kann.  
  
 Um die Wiederherstellungszeit zu reduzieren, sollten Sie komprimierte Sicherungen verwenden.  Falls die Sicherungsdatei größer als 25 GB ist, verwenden Sie das Dienstprogramm [AzCopy](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx) zum Herunterladen auf den lokalen Datenträger, und führen Sie dann die Wiederherstellung durch. Weitere bewährte Methoden und Empfehlungen zu Sicherungen finden Sie unter [SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung](sql-server-backup-to-url-best-practices-and-troubleshooting.md).  
  
 Sie können beim Ausführen der Wiederherstellung auch das Ablaufverfolgungsflag 3051 aktivieren, um ein ausführlicheres Protokoll zu generieren. Diese Protokolldatei wird im Protokollverzeichnis gespeichert und ist mit dem Namen im Format: Backuptourl-\<Instancename >-\<Dbname > - Aktion -\<PID >. Log. Die Protokolldatei enthält Informationen über jeden Roundtrip zum Windows Azure-Speicher, einschließlich Zeitangaben, die hilfreich bei der Problemdiagnose sein können.  
  
### <a name="topics-on-performing-restore-operations"></a>Themen über die Durchführung von Wiederherstellungsvorgängen  
  
-   [Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](complete-database-restores-simple-recovery-model.md)  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [Vollständige Datenbankwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](complete-database-restores-full-recovery-model.md)  
  
-   [Dateiwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](file-restores-simple-recovery-model.md)  
  
-   [Dateiwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](file-restores-full-recovery-model.md)  
  
-   [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
