---
title: Anfügen einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c7b7588801419f57d04996d6bd2cad335a9eede
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583229"
---
# <a name="attach-a-database"></a>Anfügen einer Datenbank
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Thema wird beschrieben, wie eine Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]angefügt wird. Sie können diese Funktion verwenden, um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zu kopieren, zu verschieben oder zu aktualisieren.  
  
##  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Die Datenbank muss zuerst getrennt werden. Wenn Sie versuchen, eine Datenbank anzufügen, die nicht getrennt wurde, wird ein Fehler zurückgegeben. Weitere Informationen finden Sie unter [Trennen einer Datenbank](../../relational-databases/databases/detach-a-database.md).  
  
-   Wenn Sie eine Datenbank anfügen, müssen alle Datendateien (MDF- und LDF-Dateien) verfügbar sein. Wenn eine Datendatei einen anderen Pfad als beim Erstellen oder beim letzten Anfügen der Datenbank aufweist, müssen Sie den aktuellen Pfad der Datei angeben.  
  
-   Wenn Sie eine Datenbank anfügen, MDF- und LDF-Dateien sich in verschiedenen Verzeichnissen befinden und einer der Pfade „ \\\\?\GlobalRoot“ enthält, schlägt der Vorgang fehl.  
  
###  <a name="Recommendations"></a> Ist Anfügen am besten geeignet?  
Es wird empfohlen, Datenbanken mit der `ALTER DATABASE`-Prozedur für geplante Verschiebungen zu verschieben, anstatt Trenn- und Anfügevorgänge zu verwenden, wenn Sie Datenbankdateien innerhalb einer Instanz verschieben. Weitere Informationen finden Sie unter [Move User Databases](../../relational-databases/databases/move-user-databases.md). 
 
Es wird davon abgeraten, Trenn- und Anfügevorgänge für Sicherungen und Wiederherstellungen zu verwenden. Es gibt keine Sicherungen von Transaktionsprotokollen, und Dateien können versehentlich gelöscht werden.
  
###  <a name="Security"></a> Sicherheit  
Dateizugriffsberechtigungen werden während einer Reihe von Datenbankvorgängen festgelegt, einschließlich des Trennens oder Anfügens einer Datenbank. Informationen zu Dateiberechtigungen, die beim Trennen und Anfügen einer Datenbank festgelegt werden, finden Sie unter [Sichern von Daten- und Protokolldateien](https://technet.microsoft.com/library/ms189128.aspx) in der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Onlinedokumentation (noch immer lesenswert). 
  
Das Anfügen oder Wiederherstellen von Datenbanken aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Solche Datenbanken können bösartigen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code ausführt oder Fehler verursacht, indem er das Schema oder die physische Datenbankstruktur ändert. Bevor Sie eine Datenbank aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, führen Sie auf einem Nichtproduktionsserver [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) für die Datenbank aus. Überprüfen Sie außerdem den Code in der Datenbank, z.B. gespeicherte Prozeduren oder anderen benutzerdefinierten Code. Weitere Informationen zum Anfügen von Datenbanken sowie Informationen zu Änderungen, die an Metadaten vorgenommen werden, wenn Sie eine Datenbank anfügen, finden Sie unter [Anfügen und Trennen von Datenbanken (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
####  <a name="Permissions"></a> Berechtigungen  
Erfordert die Berechtigung `CREATE DATABASE`, `CREATE ANY DATABASE` oder `ALTER ANY DATABASE`.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  

### <a name="to-attach-a-database"></a>So fügen Sie eine Datenbank an  
  
1.  Stellen Sie im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und klicken Sie dann, um diese Instanzansicht in SSMS zu erweitern.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datenbanken** , und klicken Sie auf **Anfügen**.  
  
3.  Wenn Sie die anzufügende Datenbank angeben möchten, klicken Sie im Dialogfeld **Datenbanken anfügen** auf **Hinzufügen**. Wählen Sie dann im Dialogfeld **Datenbankdateien suchen** den Datenträger aus, auf dem die Datenbank gespeichert ist. Erweitern Sie die Verzeichnisstruktur, um die MDF-Datei der Datenbank zu suchen und auszuwählen. Beispiel:  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > Trying to select a database that is already attached generates an error.  
  
     **Databases to attach**  
     Displays information about the selected databases.  
  
     \<no column header>  
     Displays an icon indicating the status of the attach operation. The possible icons are described in the **Status** description, below).  
  
     **MDF File Location**  
     Displays the path and file name of the selected MDF file.  
  
     **Database Name**  
     Displays the name of the database.  
  
     **Attach As**  
     Optionally, specifies a different name for the database to attach as.  
  
     **Owner**  
     Provides a drop-down list of possible database owners from which you can optionally select a different owner.  
  
     **Status**  
     Displays the status of the database according to the following table.  
  
    |Symbol|Statustext|und Beschreibung|  
    |----------|-----------------|-----------------|  
    |(Kein Symbol)|(Kein Text)|Das Anfügen hat noch nicht begonnen oder steht für dieses Objekt noch aus. Dies ist der Standardwert bei Öffnen des Dialogfelds.|  
    |Grünes, nach rechts zeigendes Dreieck|Vorgang wird ausgeführt|Das Anfügen hat begonnen, ist aber noch nicht abgeschlossen.|  
    |Grünes Häkchen|Success|Das Objekt wurde erfolgreich angefügt.|  
    |Roter Kreis mit einem weißen Kreuz darin|Fehler|Beim Anfügen ist ein Fehler aufgetreten. Der Vorgang konnte deshalb nicht erfolgreich abgeschlossen werden.|  
    |Kreis mit zwei schwarzen Quadranten (links und rechts) und zwei weißen Quadranten (oben und unten) darin|Beendet|Das Anfügen wurde nicht erfolgreich abgeschlossen, weil der Benutzer den Vorgang angehalten hat.|  
    |Kreis mit einem gekrümmten Pfeil darin, der entgegengesetzt der Uhrzeigerrichtung zeigt|Rollback wurde ausgeführt|Anfügen war erfolgreich, es wurde jedoch ein Rollback durchgeführt, weil beim Anfügen eines anderen Objekts ein Fehler aufgetreten ist.|  
  
     **Message**  
     Displays either a blank message or a "File not found" hyperlink.  
  
     **Add**  
     Find the necessary main database files. When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.  
  
     **Remove**  
     Removes the selected file from the **Databases to attach** grid.  
  
     **"** *<database_name>* **" database details**  
     Displays the names of the files to be attached. To verify or change the pathname of a file, click the **Browse** button (**...**).  
  
    > [!NOTE]  
    > If a file does not exist, the **Message** column displays "Not found." If a log file is not found, it exists in another directory or has been deleted. You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid. If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.  
  
     **Original File Name**  
     Displays the name of the attached file belonging to the database.  
  
     **File Type**  
     Indicates the type of file, **Data** or **Log**.  
  
     **Current File Path**  
     Displays the path to the selected database file. The path can be edited manually.  
  
     **Message**  
     Displays either a blank message or a "**File not found**" hyperlink.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
### <a name="to-attach-a-database"></a>So fügen Sie eine Datenbank an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Verwenden Sie die Anweisung [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) mit der `FOR ATTACH`-Klausel.  
  
     Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel werden die Dateien der Datenbank [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] angefügt, und die Datenbank wird in `MyAdventureWorks`umbenannt.  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > Alternativ können Sie die gespeicherte Prozedur [sp_attach_db](../../relational-databases/system-stored-procedures/sp-attach-db-transact-sql.md) oder [sp_attach_single_file_db](../../relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql.md) verwenden. Diese Prozeduren werden jedoch in einer zukünftigen Version von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Stattdessen wird die Verwendung von `CREATE DATABASE ... FOR ATTACH` empfohlen.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Aktualisieren einer SQL Server-Datenbank  
Nachdem Sie eine Datenbank mithilfe der Anfügemethode aktualisiert haben, ist die Datenbank sofort verfügbar und wird automatisch aktualisiert. Wenn die Datenbank Volltextindizes aufweist, werden diese beim Upgrade importiert, zurückgesetzt oder neu erstellt, je nach der Einstellung der Servereigenschaft **Volltextupgrade-Option** . Wenn die Upgradeoption auf **Importieren** oder **Neu erstellen**festgelegt ist, sind die Volltextindizes während des Upgrades nicht verfügbar. Je nach Menge der indizierten Daten kann der Importvorgang mehrere Stunden dauern; die Neuerstellung sogar bis zu zehnmal länger. Wenn die Upgradeoption auf **Importieren**festgelegt und kein Volltextkatalog verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt.  
  
War der Kompatibilitätsgrad einer Benutzerdatenbank vor dem Upgrade 100 oder höher, wird er nach dem Upgrade beibehalten. War der Kompatibilitätsgrad der aktualisierten Datenbank vor dem Upgrade 90, wird er auf 100 gesetzt, was dem niedrigsten unterstützten Kompatibilitätsgrad in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] entspricht. Weitere Informationen finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
> [!NOTE]
> Wenn Sie eine Datenbank aus einer Instanz anfügen, die unter [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] oder älter ausgeführt wurde und für die Change Data Capture (CDC) aktiviert war, müssen Sie auch den unten genannten Befehl ausführen, um die Metadaten von CDC upzugraden.
  
```sql
USE <database name>
EXEC sys.sp_cdc_vupgrade  
``` 
 
## <a name="see-also"></a>Weitere Informationen  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md) 
 <br>[Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einem anderen Server](manage-metadata-when-making-a-database-available-on-another-server.md)  
 [Trennen einer Datenbank](../../relational-databases/databases/detach-a-database.md)  
  
  
