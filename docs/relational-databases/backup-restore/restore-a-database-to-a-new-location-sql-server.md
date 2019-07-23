---
title: Wiederherstellen einer Datenbank an einem neuen Speicherort (SQL Server) | Microsoft-Datenbank
ms.custom: ''
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], moving
- database restores [SQL Server], creating new databases
- restoring [SQL Server], with move
- restoring databases [SQL Server], creating new databases
- database backups [SQL Server], creating new database from
- backing up databases [SQL Server], creating new database from
- restoring databases [SQL Server], renaming
- database creation [SQL Server], restoring with move
ms.assetid: 4da76d61-5e11-4bee-84f5-b305240d9f42
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bef38ae0b93eb43d508192c6f748a36320143689
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937539"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a>Wiederherstellen einer Datenbank an einem neuen Speicherort (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von SQL Server Management Studio(SSMS) oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Datenbank an einem neuen Speicherort wiederherstellen und sie optional umbenennen können. Sie können eine Datenbank in ein neues Verzeichnis verschieben oder eine Kopie einer Datenbank entweder auf der gleichen oder einer anderen Serverinstanz erstellen.  
    
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Nur der Systemadministrator, der eine vollständige Datenbanksicherung wiederherstellt, darf die wiederherzustellende Datenbank aktuell verwenden.  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Im vollständigen oder im massenprotokollierten Wiederherstellungsmodell muss das Protokoll der aktiven Transaktion gesichert werden, bevor eine Datenbank wiederhergestellt werden kann. Weitere Informationen finden Sie unter [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)-Datenbank an einem neuen Speicherort wiederherstellen und sie optional umbenennen können.  

-   Um eine verschlüsselte Datenbank wiederherzustellen, **benötigen Sie Zugriff auf das Zertifikat oder den asymmetrischen Schlüssel, der zum Verschlüsseln der Datenbank verwendet wurde.** Ohne dieses Zertifikat oder den asymmetrischen Schlüssel können Sie die Datenbank nicht wiederherstellen. Sie müssen das zum Verschlüsseln des Datenbankverschlüsselungsschlüssels verwendete Zertifikat so lange aufbewahren, wie Sie die Sicherung benötigen. Weitere Informationen finden Sie unter [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Weitere Überlegungen zum Verschieben einer Datenbank finden Sie unter [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../../relational-databases/databases/copy-databases-with-backup-and-restore.md).  
  
-   Wenn Sie eine Datenbank aus [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (oder höher) oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wiederherstellen, wird die Datenbank automatisch aktualisiert. In der Regel ist die Datenbank sofort verfügbar. Wenn eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbank aber Volltextindizes aufweist, werden diese beim Upgrade entweder importiert, zurückgesetzt oder neu erstellt, je nach der Einstellung der Servereigenschaft  **upgrade_option** . Wenn die Upgradeoption auf „Importieren“ (**upgrade_option** = 2) oder „Neu erstellen“ (**upgrade_option** = 0) festgelegt ist, sind die Volltextindizes während des Upgrades nicht verfügbar. Je nach Menge der indizierten Daten kann der Importvorgang mehrere Stunden dauern; die Neuerstellung sogar bis zu zehnmal länger. Wenn die Upgradeoption auf Importieren festgelegt ist und kein Volltextkatalog verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt. Verwenden Sie **sp_fulltext_service** , um die Einstellung der Servereigenschaft [upgrade_option](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)zu ändern.  
  
###  <a name="Security"></a> Sicherheit  
 Aus Sicherheitsgründen empfiehlt es sich nicht, Datenbanken aus unbekannten oder nicht vertrauenswürdigen Quellen anzufügen oder wiederherzustellen. Solche Datenbanken können bösartigen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code ausführt oder Fehler verursacht, indem er das Schema oder die physische Datenbankstruktur ändert. Bevor Sie eine Datenbank aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, führen Sie auf einem Nichtproduktionsserver [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) für die Datenbank aus. Überprüfen Sie außerdem den Code in der Datenbank, z.B. gespeicherte Prozeduren oder anderen benutzerdefinierten Code.  
  
####  <a name="Permissions"></a> Berechtigungen  
 Ist die wiederherzustellende Datenbank nicht vorhanden, muss der Benutzer über CREATE DATABASE-Berechtigungen verfügen, um RESTORE ausführen zu können. Ist die Datenbank vorhanden, werden RESTORE-Berechtigungen standardmäßig den Mitgliedern der festen Serverrollen **sysadmin** und **dbcreator** sowie dem Besitzer (**dbo**) der Datenbank erteilt.  
  
 RESTORE-Berechtigungen werden Rollen erteilt, in denen Mitgliedsinformationen immer für den Server verfügbar sind. Da die Mitgliedschaft in einer festen Datenbankrolle nur bei unbeschädigten und zugänglichen Datenbanken geprüft werden kann (was beim Ausführen von RESTORE nicht immer der Fall ist), verfügen Mitglieder der festen Datenbankrolle **db_owner** nicht über RESTORE-Berechtigungen.  
  
  
## <a name="restore-a-database-to-a-new-location-optionally-rename-the-database-using-ssms"></a>Wiederherstellen einer Datenbank an einem neuen Speicherort; optionales Umbenennen der Datenbank mithilfe von SSMS 

  
1.  Stellen Sie eine Verbindung mit der entsprechenden Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und klicken Sie danach im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie anschließend auf **Datenbank wiederherstellen**. Das Dialogfeld **Datenbank wiederherstellen** wird geöffnet.  
  
3.  Legen Sie Quelle und Speicherort der wiederherzustellenden Sicherungssätze auf der Seite **Allgemein** mithilfe des Abschnitts **Quelle** fest. Wählen Sie eine der folgenden Optionen aus:  
  
    -   **Datenbank**  
  
         Wählen Sie die wiederherzustellende Datenbank aus der Dropdownliste aus. Die Liste enthält nur Datenbanken, die entsprechend dem Sicherungsverlauf von **msdb** gesichert wurden.  
  
    > **HINWEIS:** Wenn die Sicherung von einem anderen Server abgerufen wird, verfügt der Zielserver über keine Sicherungsverlaufsinformationen für die angegebene Datenbank. Wählen Sie in diesem Fall **Sicherungsmedium** aus, um die wiederherzustellende Datei oder das Medium manuell anzugeben.  
  
    1.  **Sicherungsmedium**  
  
         Klicken Sie auf die Schaltfläche zum Durchsuchen ( **...** ), um das Dialogfeld **Sicherungsmedien auswählen** zu öffnen. Wählen Sie im Feld **Sicherungsmedientyp** einen der aufgeführten Medientypen aus. Wenn Sie ein oder mehrere Medien für das Feld **Sicherungsmedien** auswählen möchten, klicken Sie auf **Hinzufügen**.  
  
         Klicken Sie nach dem Hinzufügen der gewünschten Medien zum Listenfeld **Sicherungsmedien** auf **OK** , um zur Seite **Allgemein** zurückzukehren.  
  
         Wählen Sie im Listenfeld **Quelle: Sicherungsmedium: Datenbank** den Namen der Datenbank aus, die wiederhergestellt werden soll.  
  
         **Hinweis** Diese Liste ist nur verfügbar, wenn **Sicherungsmedium** ausgewählt wird. Nur Datenbanken mit Sicherungen auf dem ausgewählten Medium stehen zur Verfügung.  
  
4.  Im Abschnitt **Ziel** wird das Feld **Datenbank** automatisch mit dem Namen der Datenbank aufgefüllt, die wiederhergestellt werden soll. Geben Sie zum Ändern des Datenbanknamens den neuen Namen ins Feld **Datenbank** ein.  
  
5.  Übernehmen Sie im Feld **Wiederherstellen in** den Standardwert **Bis zur zuletzt erstellten Sicherung** , oder klicken Sie auf **Zeitachse** , um auf das Dialogfeld **Sicherungszeitachse** zuzugreifen und darin manuell einen Zeitpunkt zum Beenden des Wiederherstellungsvorgangs auszuwählen. Weitere Informationen zum Festlegen eines bestimmten Zeitpunkts finden Sie unter [Backup Timeline](../../relational-databases/backup-restore/backup-timeline.md) .  
  
6.  Wählen Sie im Raster **Wiederherzustellende Sicherungssätze** die wiederherzustellenden Sicherungen aus. Mit diesem Raster werden die Sicherungen angezeigt, die für den angegebenen Speicherort verfügbar sind. Standardmäßig wird ein Wiederherstellungsplan vorgeschlagen. Sie können die Auswahl im Raster ändern, um den vorgeschlagenen Wiederherstellungsplan zu überschreiben. Die Auswahl von Sicherungen, die von der Wiederherstellung einer früheren Sicherung abhängig sind, wird automatisch aufgehoben, wenn die Auswahl der früheren Sicherung aufgehoben wird.  
  
     Weitere Informationen zu den Spalten des Rasters **Wiederherzustellende Sicherungssätze** finden Sie unter [Datenbank wiederherstellen &#40;Seite „Allgemein“&#41;](../../relational-databases/backup-restore/restore-database-general-page.md).  
  
7.  Wählen Sie zum Angeben des neuen Speicherorts der Datenbankdateien die Seite **Dateien** , und klicken Sie anschließend auf **Alle Dateien verschieben in Ordner**. Geben Sie einen neuen Speicherort für die Ordner **Datendatei** und **Protokolldatei**an. Weitere Informationen zu diesem Raster finden Sie unter [Datenbank wiederherstellen &#40;Seite Dateien&#41;](../../relational-databases/backup-restore/restore-database-files-page.md).  
  
8.  Passen Sie ggf. die Optionen auf der Seite **Optionen** an. Weitere Informationen zu diesen Optionen finden Sie unter [Datenbank wiederherstellen &#40;Seite „Optionen“&#41;](../../relational-databases/backup-restore/restore-database-options-page.md).  

 ## <a name="restore-database-to-a-new-location-optionally-rename-the-database-using-t-sql"></a>Wiederherstellen einer Datenbank an einem neuen Speicherort; optionales Umbenennen der Datenbank mithilfe von T-SQL
 
 
1.  Legen Sie optional den logischen und den physischen Namen der Dateien in dem Sicherungssatz fest, der die vollständige Datenbanksicherung enthält, die Sie wiederherstellen möchten. Diese Anweisung gibt eine Liste mit Datenbank- und Protokolldateien zurück, die im Sicherungssatz enthalten sind. Die Basissyntax lautet wie folgt:  
  
     RESTORE FILELISTONLY FROM *<Sicherungsmedium>* WITH FILE = *backup_set_file_number* 
  
     Dabei gibt *backup_set_file_number* die Position der Sicherung im Mediensatz an. Sie können die Position eines Sicherungssatzes mithilfe der [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) -Anweisung abrufen. Weitere Informationen finden Sie unter [RESTORE-Argumente &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md) im Abschnitt „Angeben eines Sicherungssatzes“.  
  
     Diese Anweisung unterstützt auch eine Reihe von WITH-Optionen. Weitere Informationen finden Sie unter [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).  
  
2.  Stellen Sie die vollständige Datenbanksicherung mithilfe der [RESTORE DATABASE](../../t-sql/statements/restore-statements-transact-sql.md) -Anweisung wieder her. Standardmäßig werden Daten und Protokolldateien an ihren ursprünglichen Speicherorten wiederhergestellt. Verwenden Sie zum Verschieben einer Datenbank die Option MOVE, um die einzelnen Datenbankdateien zu verschieben und Konflikte mit vorhandenen Dateien zu vermeiden.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for restoring the database to a new location and a new name is:  
  
     RESTORE DATABASE *new_database_name*  
  
     FROM *backup_device* [ ,...*n* ]  
  
     [ WITH  
  
     {  
  
     [ **RECOVERY** | NORECOVERY ]  
  
     [ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]  
  
     [ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]  
  
     }  
  
     ;  
  
    > **NOTE!** When preparing to relocate a database on a different disk, you should verify that sufficient space is available and identify any potential collisions with existing files. This involves using a [RESTORE VERIFYONLY](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md) statement that specifies the same MOVE parameters that you plan to use in your RESTORE DATABASE statement.  
  
     The following table describes arguments of this RESTORE statement in terms of restoring a database to a new location. For more information about these arguments, see [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).  
  
     *new_database_name*  
     The new name for the database.  
  
    >**NOTE:** If you are restoring the database to a different server instance, you can use the original database name instead of a new name.  
  
     *backup_device* [ **,**...*n* ]  
     Specifies a comma-separated list of from 1 to 64 backup devices from which the database backup is to be restored. You can specify a physical backup device, or you can specify a corresponding logical backup device, if defined. To specify a physical backup device, use the DISK or TAPE option:  
  
     { DISK | TAPE } **=**_physical_backup_device_name_  
  
     For more information, see [Backup Devices &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
     { **RECOVERY** | NORECOVERY }  
     If the database uses the full recovery model, you might need to apply transaction log backups after you restore the database. In this case, specify the NORECOVERY option.  
  
     Otherwise, use the RECOVERY option, which is the default.  
  
     FILE = { *backup_set_file_number* | @*backup_set_file_number* }  
     Identifies the backup set to be restored. For example, a *backup_set_file_number* of **1** indicates the first backup set on the backup medium and a *backup_set_file_number* of **2** indicates the second backup set. You can obtain the *backup_set_file_number* of a backup set by using the [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) statement.  
  
     When this option is not specified, the default is to use the first backup set on the backup device.  
  
     For more information, see "Specifying a Backup Set," in [RESTORE Arguments &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
     MOVE **'**_logical_file_name_in_backup_**'** TO **'**_operating_system_file_name_**'** [ **,**...*n* ]  
     Specifies that the data or log file specified by *logical_file_name_in_backup* is to be restored to the location specified by *operating_system_file_name*. Specify a MOVE statement for every logical file you want to restore from the backup set to a new location.  
  
    |Option|und Beschreibung|  
    |------------|-----------------|  
    |*logical_file_name_in_backup*|Gibt den logischen Namen einer Daten- oder Protokolldatei an, die in den Sicherungssatz eingeschlossen werden soll. Der logische Dateiname einer Daten- oder Protokolldatei in einem Sicherungssatz entspricht ihrem logischen Namen in der Datenbank zum Zeitpunkt der Erstellung des Sicherungssatzes.<br /><br /> <br /><br /> Hinweis: Mit [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md) können Sie eine Liste abrufen, in der die logischen Dateien eines Sicherungssatzes aufgeführt sind.|  
    |*operating_system_file_name*|Gibt einen neuen Speicherort für die von *logical_file_name_in_backup*angegebene Datei an. Die Datei wird an diesem Speicherort wiederhergestellt.<br /><br /> Optional gibt *operating_system_file_name* einen neuen Dateinamen für die wiederhergestellte Datei an. Dies ist erforderlich, wenn Sie eine Kopie einer vorhandenen Datenbank auf der gleiche Serverinstanz erstellen.|  
    |*n*|Ist ein Platzhalter, der angibt, dass weitere MOVE-Anweisungen angegeben werden können.|  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 In diesem Beispiel wird eine neue Datenbank mit dem Namen `MyAdvWorks` erstellt, indem eine Sicherung der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank wiederhergestellt wird, die zwei Dateien einschließt: [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data und [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log. Für diese Datenbank wird das einfache Wiederherstellungsmodell verwendet. Die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank ist bereits auf der Serverinstanz vorhanden, sodass die Dateien in der Sicherung an einem neuen Ort wiederhergestellt werden müssen. Die RESTORE FILELISTONLY-Anweisung wird verwendet, um die Anzahl und die Namen der Dateien der Datenbank zu bestimmen, die wiederhergestellt werden. Die Datenbanksicherung ist der erste Sicherungssatz auf dem Sicherungsmedium.  
  
> **HINWEIS:** In den Beispielen zum Sichern und Wiederherstellen des Transaktionsprotokolls (einschließlich der Zeitpunktwiederherstellungen) wird, wie im folgenden `MyAdvWorks_FullRM` -Beispiel, die aus [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] erstellte `MyAdvWorks` -Datenbank verwendet. Die resultierende `MyAdvWorks_FullRM`-Datenbank muss jedoch dahingehend geändert werden, dass das vollständige Wiederherstellungsmodell mit der folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung verwendet wird: ALTER DATABASE <database_name> SET RECOVERY FULL.  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
-- AdventureWorks2012_Backup is the name of the backup device.  
RESTORE FILELISTONLY  
   FROM AdventureWorks2012_Backup;  
-- Restore the files for MyAdvWorks.  
RESTORE DATABASE MyAdvWorks  
   FROM AdventureWorks2012_Backup  
   WITH RECOVERY,  
   MOVE 'AdventureWorks2012_Data' TO 'D:\MyData\MyAdvWorks_Data.mdf',   
   MOVE 'AdventureWorks2012_Log' TO 'F:\MyLog\MyAdvWorks_Log.ldf';  
GO  
  
```  
  
 Ein Beispiel für das Erstellen einer vollständigen Sicherung der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank finden Sie unter [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)-Datenbank an einem neuen Speicherort wiederherstellen und sie optional umbenennen können.  
  
##  <a name="RelatedTasks"></a> Related tasks  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Serverinstanz &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)  
  
  
