---
title: Erstellen einer vollständigen Datenbanksicherung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9e1daefbc5625aaf034a9be9218a59daf5286cc1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094024"
---
# <a name="create-a-full-database-backup-sql-server"></a>Erstellen einer vollständigen Datenbanksicherung (SQL Server)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder PowerShell eine vollständige Datenbanksicherung erstellen.  
  
> [!NOTE]  
>  Informationen zur SQL Server-Sicherung im Windows Azure-BLOB-Speicherdienst finden Sie unter [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **Zum Erstellen einer vollständigen Datenbank datenbanksicherung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die BACKUP-Anweisung ist nicht in einer expliziten oder implizierten Transaktion zulässig.  
  
-   Sicherungen, die mit aktuelleren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt werden, können in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nicht wiederhergestellt werden.  
  
-   Weitere Informationen finden Sie unter [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md).  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Wenn eine Datenbank größer wird, ist zum Abschließen von vollständigen Datenbanksicherungen jedoch mehr Zeit und mehr Speicherplatz erforderlich. Deshalb können Sie bei einer großen Datenbank eine vollständige Datenbanksicherung durch mehrere *differenzielle Datenbanksicherungen*ergänzen. Weitere Informationen finden Sie unter [Differenzielle Sicherungen &#40;SQL Server&#41;](differential-backups-sql-server.md).  
  
-   Ein Schätzwert der Größe einer vollständigen Datenbanksicherung kann mithilfe der gespeicherten Systemprozedur [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) ermittelt werden.  
  
-   Standardmäßig wird bei jedem erfolgreichen Sicherungsvorgang dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und dem Systemereignisprotokoll ein Eintrag hinzugefügt. Wenn Sie das Protokoll regelmäßig sichern, kann die Anzahl dieser Erfolgsmeldungen schnell ansteigen, d. h., es entstehen sehr große Fehlerprotokolle, die das Suchen nach anderen Meldungen erschweren können. In solchen Fällen können Sie diese Protokolleinträge mithilfe des Ablaufverfolgungsflags 3226 unterdrücken, wenn keines der Skripts von diesen Einträgen abhängig ist. Weitere Informationen finden Sie unter [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="Security"></a> Sicherheit  
 Bei einer Datenbanksicherung ist TRUSTWORTHY auf OFF festgelegt. Weitere Informationen zum Festlegen von TRUSTWORTHY auf ON finden Sie unter [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
 Beginnend mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] der `PASSWORD` und `MEDIAPASSWORD` -Optionen nicht mehr zum Erstellen von Sicherungen. Sie können jedoch immer noch mit Kennwörtern erstellte Sicherungen wiederherstellen.  
  
####  <a name="Permissions"></a> Berechtigungen  
 Mitglieder der festen Serverrolle **sysadmin** und der festen Datenbankrollen **db_owner** und **db_backupoperator** verfügen standardmäßig über BACKUP DATABASE- und BACKUP LOG-Berechtigungen.  
  
 Besitz- und Berechtigungsprobleme im Zusammenhang mit der physischen Datei des Sicherungsmediums können den Sicherungsvorgang beeinträchtigen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss über Lese- und Schreibberechtigungen für das Medium verfügen. Das Konto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst ausgeführt wird, muss Schreibberechtigungen haben. Allerdings prüft die gespeicherte Prozedur [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), die den Systemtabellen einen Eintrag für ein Sicherungsmedium hinzufügt, nicht die Dateizugriffsberechtigungen. Solche Probleme mit der physischen Datei des Sicherungsmediums treten möglicherweise erst auf, wenn auf die physische Ressource zugegriffen wird, um einen Sicherungs- oder Wiederherstellungsvorgang auszuführen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
> [!NOTE]  
>  Wenn Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Sicherungstask angeben, können Sie das entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql)-Skript generieren, indem Sie auf die Schaltfläche **Skript** klicken und ein Ziel für das Skript auswählen.  
  
#### <a name="to-back-up-a-database"></a>So sichern Sie eine Datenbank  
  
1.  Klicken Sie im Objekt-Explorer nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie den Ordner **Datenbanken**, und wählen Sie dann je nach Datenbank entweder eine Benutzerdatenbank aus, oder erweitern Sie die Option **Systemdatenbanken** , um eine Systemdatenbank auszuwählen.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Tasks**, und klicken Sie dann auf **Sichern**. Das Dialogfeld **Datenbank sichern** wird angezeigt.  
  
4.  In der `Database` Listenfeld, überprüfen Sie den Datenbanknamen. Sie können optional eine andere Datenbank aus der Liste auswählen.  
  
5.  Eine Datenbanksicherung kann für jedes Wiederherstellungsmodell ausgeführt werden (**FULL**, **BULK_LOGGED**oder **SIMPLE**).  
  
6.  Wählen Sie im Listenfeld **Sicherungstyp** die Option **Vollständig**aus.  
  
     Beachten Sie, dass Sie nach dem Erstellen einer vollständigen Datenbanksicherung eine differenzielle Datenbanksicherung ausführen können. Weitere Informationen finden Sie unter [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).  
  
7.  Sie können optional auch **Kopiesicherung** auswählen, um eine Kopiesicherung zu erstellen. Eine *Kopiesicherung* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung, die unabhängig von der Sequenz von herkömmlichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen erstellt wird. Weitere Informationen finden Sie unter [Kopiesicherungen &#40;SQL Server&#41;](copy-only-backups-sql-server.md).  
  
    > [!NOTE]  
    >  Wenn die Option **Differenziell** aktiviert ist, können Sie keine Kopiesicherung erstellen.  
  
8.  Für **Sicherungskomponente**, klicken Sie auf `Database`.  
  
9. Akzeptieren Sie entweder den im Textfeld **Name** vorgeschlagenen Standardnamen für den Sicherungssatz, oder geben Sie einen anderen Namen für den Sicherungssatz ein.  
  
10. Geben Sie optional in das Textfeld **Beschreibung** eine Beschreibung des Sicherungssatzes ein.  
  
11. Wählen Sie den Sicherungszieltyp aus, indem Sie auf **Datenträger**, **Band** oder **URL**klicken. Klicken Sie auf **Hinzufügen**, um die Pfade von bis zu 64 Datenträgern oder Bandlaufwerken, die einen einzelnen Mediensatz enthalten, auszuwählen. Die ausgewählten Pfade werden im Listenfeld **Sichern auf** angezeigt.  
  
     Um einen Sicherungsziel zu entfernen, wählen Sie ihn aus, und klicken Sie auf **Entfernen**. Zum Anzeigen des Inhalts eines Sicherungsziels wählen Sie es aus, und klicken Sie auf **Inhalt**.  
  
12. Klicken Sie im Bereich **Seite auswählen** auf **Medienoptionen** , um die Medienoptionen anzuzeigen oder auszuwählen.  
  
13. Wählen Sie eine Option von **Medium überschreiben** aus, indem Sie auf eine der folgenden Optionen klicken:  
  
    -   **Auf vorhandenen Mediensatz sichern**  
  
         Klicken Sie bei dieser Option entweder auf **An vorhandenen Sicherungssatz anfügen** oder auf **Alle vorhandenen Sicherungssätze überschreiben**. Weitere Informationen finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md):  
  
         Sie können bei Bedarf das Kontrollkästchen **Mediensatznamen und Ablaufzeit des Sicherungssatzes überprüfen** aktivieren, damit beim Sicherungsvorgang das Datum und die Uhrzeit überprüft werden, an dem bzw. zu der der Mediensatz und der Sicherungssatz ablaufen.  
  
         Geben Sie optional einen Namen im Textfeld **Mediensatzname** ein. Wenn kein Name angegeben wurde, wird ein Mediensatz mit leerem Namen erstellt. Wenn Sie einen Mediensatznamen angeben, wird überprüft, ob der tatsächliche Name des Mediums (Band oder Datenträger) mit dem eingegebenen Namen übereinstimmt.  
  
        > [!IMPORTANT]  
        >  Diese Option ist deaktiviert, wenn Sie **URL** auf der Seite **Allgemein** als Sicherungsziel ausgewählt haben. Weitere Informationen finden Sie unter [Datenbank sichern &#40;Seite 'Medienoptionen'&#41;](back-up-database-media-options-page.md).  
        >   
        >  Wenn Sie die Verschlüsselung verwenden möchten, sollten Sie diese Option nicht aktivieren. Wenn Sie diese Option aktivieren, werden die Verschlüsselungsoptionen auf der Seite **Sicherungsoptionen** deaktiviert. Die Verschlüsselung wird nicht unterstützt, wenn Sie Sicherungen an den vorhandenen Sicherungssatz anfügen.  
  
    -   **Auf neuen Mediensatz sichern und alle vorhandenen Sicherungssätze löschen**  
  
         Geben Sie bei dieser Option einen Namen in das Textfeld **Name für neuen Mediensatz** und optional eine Beschreibung des Mediensatzes in das Textfeld **Beschreibung für neuen Mediensatz** ein.  
  
        > [!IMPORTANT]  
        >  Diese Option ist deaktiviert, wenn Sie auf der Seite **Allgemein** die Option **URL** ausgewählt haben. Diese Aktionen werden bei einer Sicherung im Windows Azure-Speicher nicht unterstützt.  
  
14. Aktivieren Sie im Abschnitt **Zuverlässigkeit** optional folgende Kontrollkästchen:  
  
    -   **Sicherung nach dem Abschluss überprüfen**.  
  
    -   **Vor dem Schreiben auf die Medien Prüfsumme bilden**, und optional **Bei Prüfsummenfehler fortsetzen**. Weitere Informationen finden Sie unter [Mögliche Medienfehler während der Sicherung und Wiederherstellung &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).  
  
15. Wenn Sie auf ein Bandlaufwerk sichern (gemäß der Konfiguration im Abschnitt **Ziel** der Seite **Allgemein**), ist die Option **Band nach dem Sichern entladen** aktiviert. Wenn Sie auf diese Option klicken, wird die Option **Band vor dem Entladen zurückspulen** aktiviert.  
  
    > [!NOTE]  
    >  Die Optionen im Abschnitt **Transaktionsprotokoll** sind inaktiv, es sei denn, Sie sichern ein Transaktionsprotokoll (wie im Abschnitt **Sicherungstyp** der Seite **Allgemein** angegeben).  
  
16. Klicken Sie im Bereich **Seite auswählen** auf **Sicherungsoptionen** , um die Sicherungsoptionen anzuzeigen und auszuwählen.  
  
17. Geben Sie an, wann der Sicherungssatz abläuft und überschrieben werden kann, ohne die Überprüfung der Ablaufdaten explizit auszulassen:  
  
    -   Wenn der Sicherungssatz nach einer bestimmten Anzahl von Tagen ablaufen soll, klicken Sie auf **Nach** (die Standardoption), und geben Sie an, nach wie vielen Tagen der Sicherungssatz abläuft. Dieser Wert kann zwischen 0 und 99999 Tagen liegen. Ein Wert von 0 Tagen bedeutet, dass der Sicherungssatz nicht abläuft.  
  
         Der Standardwert wird in der Option **Standardbeibehaltung für Sicherungsmedien (in Tagen)** des Dialogfelds **Servereigenschaften** (Seite „Datenbankeinstellungen“) festgelegt. Klicken Sie hierzu mit der rechten Maustaste auf den Servernamen im Objekt-Explorer, und wählen Sie Eigenschaften aus. Wählen Sie anschließend die Seite **Datenbankeinstellungen** aus.  
  
    -   Zum Speichern des Sicherungssatzes an einem bestimmten Datum klicken Sie auf **Am**. Geben Sie das Datum ein, an dem der Sicherungssatz abläuft.  
  
         Weitere Informationen zum Ablaufdatum von Sicherungen finden Sie unter [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql):  
  
18. [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] und höheren Versionen wird die [Sicherungskomprimierung](backup-compression-sql-server.md). Ob eine Sicherung standardmäßig komprimiert wird, ist abhängig vom Wert der Serverkonfigurationsoption **backup-compression default** . Sie können jedoch unabhängig von der aktuellen Standardeinstellung auf Serverebene eine Sicherung komprimieren, indem Sie die Option **Sicherung komprimieren**aktivieren, oder die Komprimierung verhindern, indem Sie die Option **Sicherung nicht komprimieren**aktivieren.  
  
     **Zum Anzeigen oder Ändern der aktuellen backup Compression default**  
  
    -   [Anzeigen oder Konfigurieren der Serverkonfigurationsoption Standardeinstellung für die Sicherungskomprimierung](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
19. Geben Sie an, ob die Sicherung verschlüsselt werden soll. Wählen Sie einen Verschlüsselungsalgorithmus für den Verschlüsselungsschritt aus, und geben Sie ein Zertifikat oder einen asymmetrischen Schlüssel aus der Liste der vorhandenen Zertifikate und asymmetrischen Schlüssel an. Die Verschlüsselung wird in SQL Server 2014 und höheren Versionen unterstützt. Weitere Informationen zu den Verschlüsselungsoptionen finden Sie unter [Datenbank sichern &#40;Seite 'Sicherungsoptionen'&#41;](back-up-database-backup-options-page.md).  
  
> [!NOTE]  
>  Alternativ können Sie den Wartungsplanungs-Assistenten zum Erstellen von Datenbanksicherungen verwenden.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-full-database-backup"></a>So erstellen Sie eine vollständige Datenbanksicherung  
  
1.  Führen Sie die BACKUP DATABASE-Anweisung aus, um die vollständige Datenbanksicherung zu erstellen, und geben Sie dabei Folgendes an:  
  
    -   Den Namen der zu sichernden Datenbank.  
  
    -   Das Sicherungsmedium, auf das die vollständige Datenbanksicherung geschrieben wird.  
  
     Die grundlegende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntax zum Erstellen einer vollständigen Datenbanksicherung lautet:  
  
     BACKUP DATABASE *database*  
  
     TO *backup_device* [ **,**...*n* ]  
  
     [ WITH *mit_Optionen* [ **,**...*o* ] ] ;  
  
    |Option|Description|  
    |------------|-----------------|  
    |*database*|Die Datenbank, für die eine Sicherungskopie erstellt werden soll.|  
    |*Sicherungsmedium* [ **,**...*n* ]|Gibt eine Liste an, die zwischen 1 und 64 Sicherungsmedien für den Sicherungsvorgang enthalten kann. Sie können ein physisches Sicherungsmedium angeben oder ein entsprechendes logisches Sicherungsmedium, sofern es bereits definiert wurde. Geben Sie das physische Sicherungsmedium mithilfe der Option DISK oder TAPE an:<br /><br /> { DISK &#124; TAPE } **=***Name_des_physischen_Sicherungsgeräts*<br /><br /> Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)aufgezeichnet wurde.|  
    |WITH *with_options* [ **,**...*o* ]|Optional geben Sie eine oder mehrere zusätzliche Optionen an, *o*. Weitere Informationen zu einigen der grundlegenden Optionen finden Sie unter Schritt 2.|  
  
2.  Geben Sie optional eine oder mehrere WITH-Optionen an. Einige der grundlegenden WITH-Optionen werden hier beschrieben. Weitere Informationen zu allen WITH-Optionen finden Sie unter [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql):  
  
    -   Grundlegender Sicherungssatz von WITH-Optionen:  
  
         { COMPRESSION | NO_COMPRESSION }  
         Nur in [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] und höher verfügbar. Gibt an, ob für diese Sicherung eine [Sicherungskomprimierung](backup-compression-sql-server.md) verwendet wird, wodurch die Standardeinstellung auf Serverebene überschrieben wird.  
  
         VERSCHLÜSSELUNG (ALGORITHMUS, SERVERZERTIFIKAT | ASYMMETRISCHER SCHLÜSSEL)  
         Nur in SQL Server 2014 und höheren Versionen geben Sie den zu verwendenden Verschlüsselungsalgorithmus und das Zertifikat oder den asymmetrischen Schlüssel an, die die Sicherheit bei der Verschlüsselung erhöhen.  
  
         Beschreibung **=** { **"*`text`*"** | **@*** Text_variable* }  
         Gibt den Text an, mit dem der Sicherungssatz beschrieben wird. Die Zeichenfolge kann maximal 255 Zeichen haben.  
  
         NAME **=** { *Name-des-Sicherungssatzes* | **@***Name-des-Sicherungssatzes_Variable* }  
         Gibt den Namen des Sicherungssatzes an. Namen können maximal 128 Zeichen haben. Wird NAME nicht angegeben, erhält der Sicherungssatz einen leeren Namen.  
  
    -   Grundlegender Sicherungssatz von WITH-Optionen:  
  
         Standardmäßig fügt BACKUP die Sicherung einem vorhandenen Mediensatz an, wobei vorhandene Sicherungssätze beibehalten werden. Verwenden Sie die NOINIT-Option, um dies explizit anzugeben. Informationen über das Anfügen an vorhandene Sicherungssätze finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md):  
  
         Verwenden Sie alternativ die FORMAT-Option, um die Sicherungsmedien zu formatieren:  
  
         FORMAT [ **,** MEDIANAME**=** { *Medienname* | **@***Medienname_variable* } ] [ **,** MEDIADESCRIPTION **=** { *Text* | **@***Textvariable* } ]  
         Verwenden Sie die FORMAT-Klausel, wenn Sie das Medium das erste Mal einsetzen oder alle vorhandenen Daten überschreiben möchten. Weisen Sie den neuen Medien optional einen Mediennamen und eine Beschreibung zu.  
  
        > [!IMPORTANT]  
        >  Gehen Sie mit den FORMAT- und INIT-Klauseln der BACKUP-Anweisung äußerst vorsichtig um, denn sie zerstören alle zuvor auf dem Sicherungsmedium gespeicherten Sicherungen.  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
  
#### <a name="a-backing-up-to-a-disk-device"></a>A. Sichern auf ein Datenträgermedium  
 In diesem Beispiel wird die gesamte [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank auf dem Datenträger gesichert, wobei mithilfe von `FORMAT` ein neuer Mediensatz erstellt wird.  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="b-backing-up-to-a-tape-device"></a>B. Sichern auf ein Bandmedium  
 Im folgenden Beispiel wird die gesamte [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank auf Band gesichert, wobei die Sicherung an vorherige Sicherungen angefügt wird.  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="c-backing-up-to-a-logical-tape-device"></a>C. Sichern auf ein logisches Bandmedium  
 Im folgenden Beispiel wird ein logisches Sicherungsmedium für ein Bandlaufwerk erstellt. Im Beispiel wird dann die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank vollständig auf diesem Medium gesichert.  
  
```tsql  
-- Create a logical backup device,   
-- AdventureWorks2012_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'AdventureWorks2012_Bak_Tape', '\\.\tape0'; USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO AdventureWorks2012_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'AdventureWorks2012_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
  
1.  Verwenden der `Backup-SqlDatabase` Cmdlet. Um ausdrücklich anzugeben, dass es sich um eine vollständige datenbanksicherung handelt, geben die **- BackupAction** Parameter mit dessen Standardwert `Database`. Dieser Parameter ist bei vollständigen Datenbanksicherungen optional.  
  
     Im folgenden Beispiel wird eine vollständige Datenbanksicherung der `MyDB` -Datenbank am standardmäßigen Sicherungsspeicherort der Serverinstanz `Computer\Instance`erstellt. Optional wird im Beispiel `-BackupAction Database` angegeben.  
  
    ```  
    --Enter this command at the PowerShell command prompt, C:\PS>  
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
    ```  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer vollständigen Datenbanksicherung (SQL Server)](create-a-full-database-backup-sql-server.md)  
  
-   [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
-   [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Wiederherstellen einer Datenbanksicherung unter dem einfachen Wiederherstellungsmodell &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [Wiederherstellen einer Datenbank bis zum Fehlerzeitpunkt im vollständigen Wiederherstellungsmodell &#40;Transact-SQL&#41;](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [Verwenden des Wartungsplanungs-Assistenten](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Datenbank sichern &#40;Seite Allgemein&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)   
 [Datenbank sichern &#40;Seite 'Sicherungsoptionen'&#41;](back-up-database-backup-options-page.md)   
 [Differenzielle Sicherungen &#40;SQL Server&#41;](differential-backups-sql-server.md)   
 [Vollständige Datenbanksicherungen &#40;SQL Server&#41;](full-database-backups-sql-server.md)  
  
  
