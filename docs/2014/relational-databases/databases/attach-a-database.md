---
title: Anfügen einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b4c9a3160224078b908059c3902e66ef59608bac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872249"
---
# <a name="attach-a-database"></a>Anfügen einer Datenbank
  In diesem Thema wird beschrieben, wie eine Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]angefügt wird. Sie können diese Funktion verwenden, um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zu kopieren, zu verschieben oder zu aktualisieren.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **Zum Anfügen einer Datenbank mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Upgrade einer Datenbank](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Die Datenbank muss zuerst getrennt werden. Wenn Sie versuchen, eine Datenbank anzufügen, die nicht getrennt wurde, wird ein Fehler zurückgegeben. Weitere Informationen finden Sie unter [Trennen einer Datenbank](detach-a-database.md).  
  
-   Wenn Sie eine Datenbank anfügen, müssen alle Datendateien (MDF- und LDF-Dateien) verfügbar sein. Wenn eine Datendatei einen anderen Pfad als beim Erstellen oder beim letzten Anfügen der Datenbank aufweist, müssen Sie den aktuellen Pfad der Datei angeben.  
  
-   Wenn Sie eine Datenbank anfügen, MDF- und LDF-Dateien sich in verschiedenen Verzeichnissen befinden und einer der Pfade „ \\\\?\GlobalRoot“ enthält, schlägt der Vorgang fehl.  
  
###  <a name="Recommendations"></a> Empfehlungen  
Es wird empfohlen, die Sie Verschieben von Datenbanken mithilfe der `ALTER DATABASE` Prozedur zur geplanten Verschiebung, anstelle von trennen und anfügen. Weitere Informationen finden Sie unter [Move User Databases](move-user-databases.md).  
  
###  <a name="Security"></a> Sicherheit  
Dateizugriffsberechtigungen werden während einer Reihe von Datenbankvorgängen festgelegt, einschließlich des Trennens oder Anfügens einer Datenbank. Informationen zu Dateiberechtigungen, die beim Trennen und Anfügen einer Datenbank festgelegt werden, finden Sie unter [Sichern von Daten- und Protokolldateien](https://technet.microsoft.com/library/ms189128.aspx) in der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Onlinedokumentation.  
  
Das Anfügen oder Wiederherstellen von Datenbanken aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Solche Datenbanken können bösartigen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code ausführt oder Fehler verursacht, indem er das Schema oder die physische Datenbankstruktur ändert. Bevor Sie eine Datenbank aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, führen Sie auf einem Nichtproduktionsserver [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) für die Datenbank aus. Überprüfen Sie außerdem den Code in der Datenbank, z.B. gespeicherte Prozeduren oder anderen benutzerdefinierten Code. Weitere Informationen zum Anfügen von Datenbanken sowie Informationen zu Änderungen, die an Metadaten durchgeführt werden, wenn Sie eine Datenbank anfügen, finden Sie unter [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).  
  
####  <a name="Permissions"></a> Berechtigungen  
Erfordert die Berechtigung `CREATE DATABASE`, `CREATE ANY DATABASE` oder `ALTER ANY DATABASE`.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
### <a name="to-attach-a-database"></a>So fügen Sie eine Datenbank an  
  
1.  Stellen Sie im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Verbindung zu einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie auf **Anfügen**.  
  
3.  Wenn Sie die anzufügende Datenbank angeben möchten, klicken Sie im Dialogfeld **Datenbanken anfügen** auf **Hinzufügen**. Wählen Sie dann im Dialogfeld **Datenbankdateien suchen** den Datenträger aus, auf dem die Datenbank gespeichert ist. Erweitern Sie die Verzeichnisstruktur, um die MDF-Datei der Datenbank zu suchen und auszuwählen. Beispiel:  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > Wenn Sie versuchen, eine Datenbank auszuwählen, die bereits angefügt wurde, wird ein Fehler generiert.  
  
     **Anzufügende Datenbanken**  
     Zeigt Informationen zu den ausgewählten Datenbanken an.  
  
     \<Keine Spaltenüberschrift>  
     Zeigt ein Symbol an, das den Status des Anfügevorgangs angibt. Die möglichen Symbole werden in der unten stehenden Beschreibung von **Status** beschrieben.  
  
     **Speicherort für MDF-Datei**  
     Zeigt den Pfad und den Dateinamen der ausgewählten MDF-Datei an.  
  
     **Database Name**  
     Zeigt den Namen der Datenbank an.  
  
     **Anfügen als**  
     Gibt wahlweise einen anderen Namen für die anzufügende Datenbank an.  
  
     **Besitzer**  
     Zeigt eine Dropdownliste mit möglichen Datenbankbesitzern an, aus der Sie wahlweise einen anderen Besitzer auswählen können.  
  
     **Status**  
     Zeigt den Status der Datenbank an (siehe folgende Tabelle).  
  
    |Symbol|Statustext|Description|  
    |----------|-----------------|-----------------|  
    |(Kein Symbol)|(Kein Text)|Das Anfügen hat noch nicht begonnen oder steht für dieses Objekt noch aus. Dies ist der Standardwert bei Öffnen des Dialogfelds.|  
    |Grünes, nach rechts zeigendes Dreieck|Vorgang wird ausgeführt|Das Anfügen hat begonnen, ist aber noch nicht abgeschlossen.|  
    |Grünes Häkchen|Erfolgreich|Das Objekt wurde erfolgreich angefügt.|  
    |Roter Kreis mit einem weißen Kreuz darin|Fehler|Beim Anfügen ist ein Fehler aufgetreten. Der Vorgang konnte deshalb nicht erfolgreich abgeschlossen werden.|  
    |Kreis mit zwei schwarzen Quadranten (links und rechts) und zwei weißen Quadranten (oben und unten) darin|Beendet|Das Anfügen wurde nicht erfolgreich abgeschlossen, weil der Benutzer den Vorgang angehalten hat.|  
    |Kreis mit einem gekrümmten Pfeil darin, der entgegengesetzt der Uhrzeigerrichtung zeigt|Rollback wurde ausgeführt|Anfügen war erfolgreich, es wurde jedoch ein Rollback durchgeführt, weil beim Anfügen eines anderen Objekts ein Fehler aufgetreten ist.|  
  
     **MessageBox**  
     Zeigt entweder eine leere Meldung oder einen "Datei nicht gefunden"-Link an.  
  
     **Hinzufügen**  
     Suchen Sie die erforderlichen Hauptdatenbankdateien. Wenn der Benutzer eine MDF-Datei auswählt, werden entsprechende Informationen automatisch in die jeweiligen Felder des Rasters **Anzufügende Datenbank** eingetragen.  
  
     **Entfernen**  
     Entfernt die ausgewählte Datei aus dem Raster **Anzufügende Datenbank** .  
  
     **"** *<database_name>* **" Datenbankdetails für**  
     Zeigt die Namen der anzufügenden Dateien an. Klicken Sie zum Überprüfen oder Ändern des Pfadnamens einer Datei auf die Schaltfläche **Durchsuchen** (**…**).  
  
    > [!NOTE]  
    > Wenn eine Datei nicht vorhanden ist, wird in der Spalte **Meldung** "Nicht gefunden" angezeigt. Wenn keine Protokolldatei gefunden wird, liegt sie in einem anderen Verzeichnis oder wurde gelöscht. Dann müssen Sie entweder den Dateipfad im Raster **Datenbankdetails** ändern, um auf den richtigen Pfad zu verweisen, oder die Protokolldatei aus dem Raster entfernen. Wenn keine .ndf-Datei gefunden wurde, müssen Sie ihren Pfad im Raster aktualisieren, um auf den richtigen Pfad zu verweisen.  
  
     **Originaldateiname**  
     Zeigt den Namen der angefügten Datei an, die zur Datenbank gehört.  
  
     **Dateityp**  
     Gibt den Dateityp an: **Datendatei** oder **Protokolldatei**.  
  
     **Aktueller Dateipfad**  
     Zeigt den Pfad zur ausgewählten Datenbankdatei an Die Pfadangabe kann manuell bearbeitet werden.  
  
     **MessageBox**  
     Zeigt entweder eine leere Meldung oder einen „**Datei nicht gefunden**“-Hyperlink an.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
### <a name="to-attach-a-database"></a>So fügen Sie eine Datenbank an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Verwenden der [CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql) -Anweisung mit der `FOR ATTACH` zu schließen.  
  
     Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel werden die Dateien der Datenbank [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] angefügt, und die Datenbank wird in `MyAdventureWorks`umbenannt.  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > Alternativ können Sie die gespeicherte Prozedur [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) oder [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) verwenden. Diese Prozeduren werden jedoch in einer zukünftigen Version von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Wir empfehlen die Verwendung von CREATE DATABASE... FOR ATTACH.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Aktualisieren einer SQL Server-Datenbank  
 zufügen nach upgrade eine Datenbank mithilfe der Attach-Methode, die Datenbank sofort verfügbar und wird automatisch aktualisiert. Wenn die Datenbank Volltextindizes aufweist, werden diese beim Upgrade entweder importiert, zurückgesetzt oder neu erstellt, je nach der Einstellung der Servereigenschaft **Volltextupgrade-Option** . Wenn die Upgradeoption auf **Importieren** oder **Neu erstellen**festgelegt ist, sind die Volltextindizes während des Upgrades nicht verfügbar. Je nach Menge der indizierten Daten kann der Importvorgang mehrere Stunden dauern; die Neuerstellung sogar bis zu zehnmal länger. Wenn die Upgradeoption auf **Importieren**festgelegt und kein Volltextkatalog verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt.  
  
War der Kompatibilitätsgrad einer Benutzerdatenbank vor dem Upgrade 100 oder höher, wird er nach dem Upgrade beibehalten. War der Kompatibilitätsgrad der aktualisierten Datenbank vor dem Upgrade 90, wird er auf 100 gesetzt, was dem niedrigsten unterstützten Kompatibilitätsgrad in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] entspricht. Weitere Informationen finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Trennen einer Datenbank](detach-a-database.md)  
  
  
