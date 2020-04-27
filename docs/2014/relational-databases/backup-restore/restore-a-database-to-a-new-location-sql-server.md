---
title: Wiederherstellen einer Datenbank an einem neuen Speicherort (SQL Server) | Microsoft-Datenbank
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 7a50004cfb39b93ecd0c144fb0d92d37545c83ee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62921182"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a>Wiederherstellen einer Datenbank an einem neuen Speicherort (SQL Server)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Datenbank auf einem neuen Speicherort wiederherstellen können und sie optional umbenennen können. Sie können eine Datenbank in ein neues Verzeichnis verschieben oder eine Kopie einer Datenbank entweder auf der gleichen oder einer anderen Serverinstanz erstellen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Voraussetzungen](#Prerequisites)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So stellen Sie eine Datenbank in einem neuen Speicherort wieder her und benennen diese optional um mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Nur der Systemadministrator, der eine vollständige Datenbanksicherung wiederherstellt, darf die wiederherzustellende Datenbank aktuell verwenden.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Im vollständigen oder im massenprotokollierten Wiederherstellungsmodell muss das Protokoll der aktiven Transaktion gesichert werden, bevor eine Datenbank wiederhergestellt werden kann. Weitere Informationen finden Sie unter [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)bezeichnet) gesichert werden.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Um eine verschlüsselte Datenbank wiederherstellen zu können, muss das Zertifikat oder der asymmetrische Schlüssel verfügbar sein, das oder der zum Verschlüsseln der Datenbank verwendet wurde. Ohne das Zertifikat oder den asymmetrischen Schlüssel kann die Datenbank nicht wiederhergestellt werden. Darum muss das Zertifikat, das zur Verschlüsselung des Verschlüsselungsschlüssels für die Datenbank verwendet wurde, so lange beibehalten werden, wie die Sicherung benötigt wird. Weitere Informationen finden Sie unter [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).  
  
-   Informationen zu weiteren Überlegungen zum Verschieben einer Datenbanken finden Sie unter [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../databases/copy-databases-with-backup-and-restore.md).  
  
-   Wenn Sie eine Datenbank aus [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (oder höher) oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wiederherstellen, wird die Datenbank automatisch aktualisiert. In der Regel ist die Datenbank sofort verfügbar. Wenn eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbank aber Volltextindizes aufweist, werden diese beim Upgrade entweder importiert, zurückgesetzt oder neu erstellt, je nach der Einstellung der Servereigenschaft  **upgrade_option** . Wenn die Upgradeoption auf „Importieren“ (**upgrade_option** = 2) oder „Neu erstellen“ (**upgrade_option** = 0) festgelegt ist, sind die Volltextindizes während des Upgrades nicht verfügbar. Je nach Menge der indizierten Daten kann der Importvorgang mehrere Stunden dauern; die Neuerstellung sogar bis zu zehnmal länger. Wenn die Upgradeoption auf Importieren festgelegt ist und kein Volltextkatalog verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt. Verwenden Sie **sp_fulltext_service** , um die Einstellung der Servereigenschaft [upgrade_option](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)zu ändern.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Aus Sicherheitsgründen empfiehlt es sich nicht, Datenbanken aus unbekannten oder nicht vertrauenswürdigen Quellen anzufügen oder wiederherzustellen. Solche Datenbanken können bösartigen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code ausführt oder Fehler verursacht, indem er das Schema oder die physische Datenbankstruktur ändert. Bevor Sie eine Datenbank aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, führen Sie auf einem Nichtproduktionsserver [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) für die Datenbank aus. Überprüfen Sie außerdem den Code in der Datenbank, z.B. gespeicherte Prozeduren oder anderen benutzerdefinierten Code.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Ist die wiederherzustellende Datenbank nicht vorhanden, muss der Benutzer über CREATE DATABASE-Berechtigungen verfügen, um RESTORE ausführen zu können. Ist die Datenbank vorhanden, werden RESTORE-Berechtigungen standardmäßig den Mitgliedern der festen Serverrollen **sysadmin** und **dbcreator** sowie dem Besitzer (**dbo**) der Datenbank erteilt.  
  
 RESTORE-Berechtigungen werden Rollen erteilt, in denen Mitgliedsinformationen immer für den Server verfügbar sind. Da die Mitgliedschaft in einer festen Datenbankrolle nur bei unbeschädigten und zugänglichen Datenbanken geprüft werden kann (was beim Ausführen von RESTORE nicht immer der Fall ist), verfügen Mitglieder der festen Datenbankrolle **db_owner** nicht über RESTORE-Berechtigungen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a>So stellen Sie eine Datenbank in einem neuen Speicherort wieder her und benennen diese optional um  
  
1.  Stellen Sie eine Verbindung mit der entsprechenden Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und klicken Sie danach im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie anschließend auf **Datenbank wiederherstellen**. Das Dialogfeld **Datenbank wiederherstellen** wird geöffnet.  
  
3.  Legen Sie Quelle und Speicherort der wiederherzustellenden Sicherungssätze auf der Seite **Allgemein** mithilfe des Abschnitts **Quelle** fest. Wählen Sie eine der folgenden Optionen aus:  
  
    -   **Datenbank**  
  
         Wählen Sie die wiederherzustellende Datenbank aus der Dropdownliste aus. Die Liste enthält nur Datenbanken, die entsprechend dem Sicherungsverlauf von **msdb** gesichert wurden.  
  
    > [!NOTE]  
    >  Wenn die Sicherung von einem anderen Server abgerufen wird, verfügt der Zielserver über keine Sicherungsverlaufsinformationen für die angegebene Datenbank. Wählen Sie in diesem Fall **Sicherungsmedium** aus, um die wiederherzustellende Datei oder das Medium manuell anzugeben.  
  
    1.  **Device**  
  
         Klicken Sie auf die Schaltfläche zum Durchsuchen (**...**), um das Dialogfeld **Sicherungsmedien auswählen** zu öffnen. Wählen Sie im Feld **Sicherungsmedientyp** einen der aufgeführten Medientypen aus. Wenn Sie ein oder mehrere Medien für das Feld **Sicherungsmedien** auswählen möchten, klicken Sie auf **Hinzufügen**.  
  
         Klicken Sie nach dem Hinzufügen der gewünschten Medien zum Listenfeld **Sicherungsmedien** auf **OK** , um zur Seite **Allgemein** zurückzukehren.  
  
         Wählen Sie im Listenfeld **Quelle: Sicherungsmedium: Datenbank** den Namen der Datenbank aus, die wiederhergestellt werden soll.  
  
         **Hinweis** Diese Liste ist nur verfügbar, wenn **Sicherungsmedium** ausgewählt wird. Nur Datenbanken mit Sicherungen auf dem ausgewählten Medium stehen zur Verfügung.  
  
4.  Im Abschnitt **Ziel** wird das Feld **Datenbank** automatisch mit dem Namen der Datenbank aufgefüllt, die wiederhergestellt werden soll. Geben Sie zum Ändern des Datenbanknamens den neuen Namen ins Feld **Datenbank** ein.  
  
5.  Übernehmen Sie im Feld **Wiederherstellen in** den Standardwert **Bis zur zuletzt erstellten Sicherung** , oder klicken Sie auf **Zeitachse** , um auf das Dialogfeld **Sicherungszeitachse** zuzugreifen und darin manuell einen Zeitpunkt zum Beenden des Wiederherstellungsvorgangs auszuwählen. Weitere Informationen zum Festlegen eines bestimmten Zeitpunkts finden Sie unter [Backup Timeline](backup-timeline.md) .  
  
6.  Wählen Sie im Raster **Wiederherzustellende Sicherungssätze** die wiederherzustellenden Sicherungen aus. Mit diesem Raster werden die Sicherungen angezeigt, die für den angegebenen Speicherort verfügbar sind. Standardmäßig wird ein Wiederherstellungsplan vorgeschlagen. Sie können die Auswahl im Raster ändern, um den vorgeschlagenen Wiederherstellungsplan zu überschreiben. Die Auswahl von Sicherungen, die von der Wiederherstellung einer früheren Sicherung abhängig sind, wird automatisch aufgehoben, wenn die Auswahl der früheren Sicherung aufgehoben wird.  
  
     Weitere Informationen zu den Spalten des Rasters **Wiederherzustellende Sicherungssätze** finden Sie unter [Datenbank wiederherstellen &#40;Seite „Allgemein“&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)bezeichnet) gesichert werden.  
  
7.  Wählen Sie zum Angeben des neuen Speicherorts der Datenbankdateien die Seite **Dateien** , und klicken Sie anschließend auf **Alle Dateien verschieben in Ordner**. Geben Sie einen neuen Speicherort für die Ordner **Datendatei** und **Protokolldatei**an. Weitere Informationen zu diesem Raster finden Sie unter [Datenbank wiederherstellen &#40;Seite „Dateien“&#41;](restore-database-files-page.md).  
  
8.  Passen Sie ggf. die Optionen auf der Seite **Optionen** an. Weitere Informationen zu diesen Optionen finden Sie unter [Datenbank wiederherstellen &#40;Seite „Optionen“&#41;](restore-database-options-page.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a>So stellen Sie eine Datenbank in einem neuen Speicherort wieder her und benennen diese optional um  
  
1.  Legen Sie optional den logischen und den physischen Namen der Dateien in dem Sicherungssatz fest, der die vollständige Datenbanksicherung enthält, die Sie wiederherstellen möchten. Diese Anweisung gibt eine Liste mit Datenbank- und Protokolldateien zurück, die im Sicherungssatz enthalten sind. Die Basissyntax lautet wie folgt:  
  
     RESTORE FILELISTONLY FROM *<Sicherungsmedium>* WITH FILE = *backup_set_file_number*  
  
     Dabei gibt *backup_set_file_number* die Position der Sicherung im Mediensatz an. Sie können die Position eines Sicherungssatzes mithilfe der [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) -Anweisung abrufen. Weitere Informationen finden Sie unter "Angeben eines Sicherungs Satzes" in [Restore Arguments &#40;Transact-SQL-&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
     Diese Anweisung unterstützt auch eine Reihe von WITH-Optionen. Weitere Informationen finden Sie unter [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).  
  
2.  Stellen Sie die vollständige Datenbanksicherung mithilfe der [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) -Anweisung wieder her. Standardmäßig werden Daten und Protokolldateien an ihren ursprünglichen Speicherorten wiederhergestellt. Verwenden Sie zum Verschieben einer Datenbank die Option MOVE, um die einzelnen Datenbankdateien zu verschieben und Konflikte mit vorhandenen Dateien zu vermeiden.  
  
     Die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Basissyntax für das Wiederherstellen der Datenbank an einem neuen Speicherort und mit neuem Name lautet wie folgt:  
  
     RESTORE DATABASE *Name der neuen Datenbank*  
  
     FROM *Sicherungsmedium* [ ,...*n* ]  
  
     [ WITH  
  
     {  
  
     [ **Wiederherstellung** | NORECOVERY  
  
     [ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]  
  
     [ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]  
  
     }  
  
     ;  
  
    > [!NOTE]  
    >  Wenn Sie sich auf das Verschieben einer Datenbank auf einen anderen Datenträger vorbereiten, sollten Sie überprüfen, ob dieser über genügend Speicherplatz verfügt und ob möglicherweise Konflikte mit vorhandenen Dateien auftreten können. Dazu müssen Sie unter anderem eine [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) -Anweisung verwenden, in der die gleichen MOVE-Parameter angegeben sind, die Sie in der RESTORE DATABASE-Anweisung verwenden möchten.  
  
     In der folgenden Tabelle werden Argumente dieser RESTORE-Anweisung im Hinblick auf das Wiederherstellen einer Datenbank an einem neuen Speicherort beschrieben. Weitere Informationen zu diesen Argumenten finden Sie unter [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)-Datenbank an einem neuen Speicherort wiederherstellen und sie optional umbenennen können.  
  
     *new_database_name*  
     Der neue Name der Datenbank.  
  
    > [!NOTE]  
    >  Wenn Sie die Datenbank auf einer anderen Serverinstanz wiederherstellen, können Sie anstelle eines neuen Namens den ursprünglichen Namen weiterverwenden.  
  
     *backup_device* [ `,`... *n* ]  
     Gibt eine durch Trennzeichen getrennte Liste von 1 bis 64 Sicherungsmedien an, von denen die Datenbanksicherung wiederhergestellt werden soll. Sie können ein physisches Sicherungsmedium angeben oder, sofern definiert, ein entsprechendes logisches Sicherungsmedium. Geben Sie das physische Sicherungsmedium mithilfe der Option DISK oder TAPE an:  
  
     { DISK | TAPE } `=`*physical_backup_device_name*  
  
     Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)aufgezeichnet wurde.  
  
     { **RECOVERY** | NORECOVERY }  
     Wenn die Datenbank das vollständige Wiederherstellungsmodell verwendet, müssen Sie möglicherweise Transaktionsprotokollsicherungen anwenden, nachdem Sie die Datenbank wiederhergestellt haben. Geben Sie in diesem Fall die Option NORECOVERY an.  
  
     Verwenden Sie andernfalls die Standardoption RECOVERY.  
  
     FILE = { *backup_set_file_number* | @*backup_set_file_number* }  
     Identifiziert den wiederherzustellenden Sicherungssatz. Wenn *backup_set_file_number* beispielsweise den Wert **1** besitzt, weist dies auf den ersten Sicherungssatz auf dem Sicherungsmedium hin. Wenn *backup_set_file_number* den Wert **2** besitzt, entspricht dies dem zweiten Sicherungssatz. Sie können die *backup_set_file_number* eines Sicherungssatzes mit der [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) -Anweisung abrufen.  
  
     Wenn diese Option nicht angegeben ist, wird in der Standardeinstellung der erste Sicherungssatz auf dem Sicherungsmedium verwendet.  
  
     Weitere Informationen finden Sie unter [RESTORE-Argumente &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) im Abschnitt „Angeben eines Sicherungssatzes“.  
  
     **'*`logical_file_name_in_backup`*'** in **'*`operating_system_file_name`*'** verschieben [ `,`... *n* ]  
     Gibt an, dass die von *logical_file_name_in_backup* angegebenen Daten oder die Protokolldatei an dem von *operating_system_file_name*angegebenen Speicherort wiederhergestellt werden sollen. Geben Sie für jede logische Datei, die aus dem Sicherungssatz an einem neuen Speicherort wiederhergestellt werden soll, eine MOVE-Anweisung an.  
  
    |Option|Beschreibung|  
    |------------|-----------------|  
    |*logical_file_name_in_backup*|Gibt den logischen Namen einer Daten- oder Protokolldatei an, die in den Sicherungssatz eingeschlossen werden soll. Der logische Dateiname einer Daten- oder Protokolldatei in einem Sicherungssatz entspricht ihrem logischen Namen in der Datenbank zum Zeitpunkt der Erstellung des Sicherungssatzes.<br /><br /> Hinweis: Mit [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)können Sie eine Liste abrufen, in der die logischen Dateien eines Sicherungssatzes aufgeführt sind.|  
    |*operating_system_file_name*|Gibt einen neuen Speicherort für die von *logical_file_name_in_backup*angegebene Datei an. Die Datei wird an diesem Speicherort wiederhergestellt.<br /><br /> Optional gibt *operating_system_file_name* einen neuen Dateinamen für die wiederhergestellte Datei an. Dies ist erforderlich, wenn Sie eine Kopie einer vorhandenen Datenbank auf der gleiche Serverinstanz erstellen.|  
    |*n*|Ist ein Platzhalter, der angibt, dass weitere MOVE-Anweisungen angegeben werden können.|  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a>Beispiel (Transact-SQL)  
 In diesem Beispiel wird eine neue Datenbank mit dem Namen `MyAdvWorks` erstellt, indem eine Sicherung der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank wiederhergestellt wird, die zwei Dateien einschließt: [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data und [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log. Für diese Datenbank wird das einfache Wiederherstellungsmodell verwendet. Die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank ist bereits auf der Serverinstanz vorhanden, sodass die Dateien in der Sicherung an einem neuen Ort wiederhergestellt werden müssen. Die RESTORE FILELISTONLY-Anweisung wird verwendet, um die Anzahl und die Namen der Dateien der Datenbank zu bestimmen, die wiederhergestellt werden. Die Datenbanksicherung ist der erste Sicherungssatz auf dem Sicherungsmedium.  
  
> [!NOTE]  
>  In den Beispielen zum Sichern und Wiederherstellen des Transaktionsprotokolls (einschließlich der Zeitpunktwiederherstellungen) wird, wie im folgenden `MyAdvWorks_FullRM` -Beispiel, die aus [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] erstellte `MyAdvWorks` -Datenbank verwendet. Die resultierende `MyAdvWorks_FullRM`-Datenbank muss jedoch dahingehend geändert werden, dass das vollständige Wiederherstellungsmodell mit der folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung verwendet wird: ALTER DATABASE <database_name> SET RECOVERY FULL.  
  
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
  
 Ein Beispiel für das Erstellen einer vollständigen Sicherung der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank finden Sie unter [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)-Datenbank an einem neuen Speicherort wiederherstellen und sie optional umbenennen können.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Server Instanz &#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../databases/copy-databases-with-backup-and-restore.md)  
  
  
