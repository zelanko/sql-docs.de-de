---
title: SQL Server-Sicherung über URLs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c1ecaf46ebf96ab5b8d06cb5eefb69ae50ff882e
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70175836"
---
# <a name="sql-server-backup-to-url"></a>SQL Server-Sicherung über URLs
  In diesem Thema werden die Konzepte, Anforderungen und Komponenten vorgestellt, die für die Verwendung des Azure-BLOB-Speicher Dienstanbieter als Sicherungs Ziel erforderlich sind. Die Sicherungs- und Wiederherstellungsfunktion sind gleich oder ähnlich wie beim Verwenden von DISK oder TAPE, mit wenigen Unterschieden. Die Unterschiede und alle wichtigen Ausnahmen sowie einige Codebeispiele werden in diesem Thema erörtert.  
  
## <a name="requirements-components-and-concepts"></a>Anforderungen, Komponenten und Konzepte  
 **In diesem Abschnitt:**  
  
-   [Sicherheit](#security)  
  
-   [Einführung in die wichtigsten Komponenten und Konzepte](#intorkeyconcepts)  
  
-   [Azure BLOB Storage-Dienst](#Blob)  
  
-   [SQL Server-Komponenten](#sqlserver)  
  
-   [Einschränkungen](#limitations)  
  
-   [Unterstützung für BACKUP-/RESTORE-Anweisungen](#Support)  
  
-   [Verwenden des Sicherungstasks in SQL Server Management Studio](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [SQL Server-Sicherung über URLs mithilfe des Wartungsplanungs-Assistenten](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [Wiederherstellen aus Azure Storage mithilfe von SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a> Sicherheit  
 Im folgenden finden Sie Sicherheitsüberlegungen und-Anforderungen beim Sichern oder Wiederherstellen von Azure BLOB Storage-Diensten.  
  
-   Beim Erstellen eines Containers für den Azure BLOB Storage-Dienst wird empfohlen, den Zugriff auf **Privat**festzulegen. Wenn Sie den Zugriff auf Privat festlegen, wird der Zugriff auf Benutzer oder Konten eingeschränkt, die die für die Authentifizierung beim Azure-Konto erforderlichen Informationen bereitstellen können.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erfordert, dass der Azure-Konto Name und die Zugriffsschlüssel Authentifizierung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Anmelde Informationen gespeichert werden. Diese Informationen werden verwendet, um beim Ausführen von Sicherungs-oder Wiederherstellungs Vorgängen bei dem Azure-Konto zu authentifizieren.  
  
-   Das zum Ausgeben von BACKUP- oder RESTORE-Befehlen verwendete Benutzerkonto sollte Mitglied der Datenbankrolle **db_backup operator** sein und über Berechtigungen zum **Ändern beliebiger Anmeldeinformationen** verfügen.  
  
###  <a name="intorkeyconcepts"></a> Einführung in die wichtigsten Komponenten und Konzepte  
 In den folgenden beiden Abschnitten werden der Azure BLOB Storage-Dienst und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die für die Sicherung oder Wiederherstellung im Azure-BLOB-Speicherdienst verwendeten Komponenten vorgestellt. Es ist wichtig, die Komponenten und die Interaktion zwischen den Komponenten zu verstehen, um eine Sicherung oder Wiederherstellung aus dem Azure-BLOB-Speicherdienst durchzuführen.  
  
 Der erste Schritt dieses Prozesses ist das Erstellen eines Azure-Kontos. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet den **Azure Storage-Kontonamen** und seine **Zugriffsschlüssel** Werte, um BLOB-BLOB-Speicherdienste zu authentifizieren und zu schreiben und zu lesen. Diese Authentifizierungsinformationen werden in den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen gespeichert und bei Sicherungs- und Wiederherstellungsvorgängen verwendet. Eine umfassende Exemplarische Vorgehensweise zum Erstellen eines Speicher Kontos und zum Durchführen einer einfachen Wiederherstellung finden [Sie unter Tutorial using Azure Storage Service for SQL Server Backup and Restore](https://go.microsoft.com/fwlink/?LinkId=271615).  
  
 ![Zuordnung von Speicherkonto zu SQL-Anmelde] Informationen (../../tutorials/media/backuptocloud-storage-credential-mapping.gif "Zuordnung von Speicherkonto zu SQL-Anmelde") Informationen  
  
###  <a name="Blob"></a>Azure BLOB Storage-Dienst  
 **Speicherkonto:** Das Speicherkonto ist der Ausgangspunkt für alle Speicherdienste. Um auf den Azure BLOB Storage-Dienst zuzugreifen, erstellen Sie zunächst ein Azure-Speicherkonto. Der **Speicherkonto Name** und seine **Zugriffsschlüssel** Eigenschaften sind erforderlich, um sich beim Azure BLOB Storage-Dienst und dessen Komponenten zu authentifizieren.  
  
 **Container:** Ein Container stellt eine Gruppierung eines Satzes von blobspeicher bereit und kann eine unbegrenzte Anzahl von blobspeicher speichern. Um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherung in den Azure-BLOB-Dienst zu schreiben, muss mindestens der Stamm Container erstellt werden.  
  
 **BLOB:** Eine Datei eines beliebigen Typs und beliebiger Größe. Es gibt zwei Typen von BLOBs, die im Azure-BLOB-Speicherdienst gespeichert werden können: Block-und seitenblobs. Bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung werden Seitenblobs als Blobtyp verwendet. BLOBs sind im folgenden URL-Format adressierbar: https://\<Storage Account >. BLOB. Core. Windows. net/\<Container >/\<BLOB >  
  
 ![Azure Blob-Speicher](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob-Speicher")  
  
 Weitere Informationen zum Azure-BLOB-Speicherdienst finden [Sie unter Verwenden des Azure BLOB Storage Dienstanbieter](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/) .  
  
 Weitere Informationen zu Seitenblobs finden Sie unter [Grundlegendes zu Block- und Seitenblobs](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx).  
  
###  <a name="sqlserver"></a> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components  
 **URL:** Eine URL gibt einen URI (Uniform Resource Identifier) für eine eindeutige Sicherungsdatei an. Mit der URL werden Speicherort und Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungsdatei angegeben. In dieser Implementierung ist die einzige gültige URL eine, die auf ein seitenblob in einem Azure-Speicherkonto verweist. Die URL muss auf ein tatsächliches BLOB, nicht nur auf einen Container verweisen. Wenn das BLOB nicht vorhanden ist, wird es erstellt. Wenn ein vorhandenes BLOB angegeben wird, tritt bei der Sicherung ein Fehler auf, es sei denn, die with Format-Option ist angegeben.  
  
> [!WARNING]  
>  Wenn Sie eine Sicherungsdatei kopieren und in den Azure-BLOB-Speicherdienst hochladen möchten, verwenden Sie seitenblob als Speicher Option. Wiederherstellungen von Blockblobs werden nicht unterstützt. Die Ausführung von RESTORE für ein Blockblob verursacht einen Fehler.  
  
 Hier ist ein Beispiel-URL-Wert: http [s]\<://ACCOUNTNAME.BLOB.Core.Windows.NET/Container\<>/filename. bak >. HTTPS ist zwar nicht erforderlich, aber empfehlenswert.  
  
 **Anmeldeinformationen:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldeinformationen sind ein Objekt zum Speichern von Authentifizierungsinformationen, die für die Verbindung mit einer Ressource außerhalb von SQL Server erforderlich sind.  Hier werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Sicherungs-und Wiederherstellungs Prozessen Anmelde Informationen für die Authentifizierung beim Azure BLOB Storage-Dienst verwendet. In den Anmeldeinformationen werden der Name des Speicherkontos und der **Zugriffsschlüssel** des Speicherkontos gespeichert. Sobald die Anmeldeinformationen erstellt wurden, müssen sie beim Ausgeben der BACKUP-/RESTORE-Anweisungen in der WITH CREDENTIAL-Option angegeben werden. Weitere Informationen zum Anzeigen, Kopieren oder erneuten Generieren von **access keys**für Speicherkonten finden Sie unter [Zugriffsschlüssel für Speicherkonten](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Schritt-für-Schritt-Anweisungen zum Erstellen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen finden Sie im Beispiel [Create a Credential](#credential) weiter unten in diesem Thema.  
  
 Weitere allgemeine Informationen über Anmeldeinformationen finden Sie unter [Anmeldeinformationen](../security/authentication-access/credentials-database-engine.md).  
  
 Informationen mit weiteren Beispielen zur Verwendung von Anmeldeinformationen finden Sie unter [Erstellen eines Proxys für den SQL Server-Agent](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
###  <a name="limitations"></a> Einschränkungen  
  
-   Das Sichern auf Premium-Speicher wird nicht unterstützt.  
  
-   Die maximal unterstützte Größe für Sicherungen beträgt 1 TB.  
  
-   Sie können BACKUP- und RESTORE-Anweisungen mithilfe von TSQL-, SMO- oder PowerShell-Cmdlets ausgeben. Eine Sicherung oder Wiederherstellung aus dem Azure-BLOB-Speicherdienst mithilfe SQL Server Management Studio Assistenten zum Sichern oder Wiederherstellen ist zurzeit nicht aktiviert.  
  
-   Das Erstellen von Namen für logische Geräte wird nicht unterstützt. Folglich ist es nicht möglich, eine URL mithilfe von sp_dumpdevice oder über SQL Server Management Studio als Sicherungsmedium hinzuzufügen.  
  
-   Das Anfügen an vorhandene Sicherungs-BLOBs wird nicht unterstützt. Sicherungen auf einem vorhandenen BLOB können nur unter Verwendung der WITH FORMAT-Option überschrieben werden.  
  
-   Sicherungen auf mehreren BLOBS in einem einzelnen Sicherungsvorgang werden nicht unterstützt. So gibt der folgende Code z. B. einen Fehler zurück:  
  
    ```  
    BACKUP DATABASE AdventureWorks2012   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'   
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'   
          WITH CREDENTIAL = 'mycredential'   
         ,STATS = 5;  
    GO  
  
    ```  
  
-   Das Angeben einer Blockgröße mit `BACKUP` wird nicht unterstützt.  
  
-   Das Angeben von `MAXTRANSFERSIZE` wird nicht unterstützt.  
  
-   Das Angeben von Optionen für Sicherungssätze, wie `RETAINDAYS` und `EXPIREDATE`, wird nicht unterstützt.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf 259 Zeichen begrenzt. Da BACKUP TO URL 36 Zeichen für die erforderlichen Elemente zur Angabe der URL (https://.blob.core.windows.net//.bak ) beansprucht, verbleiben insgesamt noch 223 Zeichen für Konto-, Container- und Blobnamen.  
  
###  <a name="Support"></a> Unterstützung für BACKUP-/RESTORE-Anweisungen  
  
|||||  
|-|-|-|-|  
|BACKUP-/RESTORE-Anweisung|Supported|Ausnahmen|Kommentare|  
|BACKUP|???|BLOCKSIZE und MAXTRANSFERSIZE werden nicht unterstützt.|WITH CREDENTIAL muss angegeben werden.|  
|RESTORE|???||WITH CREDENTIAL muss angegeben werden.|  
|RESTORE FILELISTONLY|???||WITH CREDENTIAL muss angegeben werden.|  
|RESTORE HEADERONLY|???||WITH CREDENTIAL muss angegeben werden.|  
|RESTORE LABELONLY|???||WITH CREDENTIAL muss angegeben werden.|  
|RESTORE VERIFYONLY|???||WITH CREDENTIAL muss angegeben werden.|  
|RESTORE REWINDONLY|???|||  
  
 Allgemeine und Syntaxinformationen zu BACKUP-Anweisungen finden Sie unter [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
 Allgemeine und Syntaxinformationen zu RESTORE-Anweisungen finden Sie unter [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).  
  
### <a name="support-for-backup-arguments"></a>Unterstützung für BACKUP-Argumente  
  
|||||  
|-|-|-|-|  
|Argument|Unterstützt|Exception|Kommentare|  
|DATABASE|???|||  
|LOG|???|||  
||  
|TO (URL)|???|Bei URL wird das Angeben bzw. Erstellen eines logischen Namens im Gegensatz zu DISK und TAPE nicht unterstützt.|Dieses Argument wird verwendet, um den URL-Pfad der Sicherungsdatei anzugeben.|  
|MIRROR TO|???|||  
|**WITH-OPTIONEN:**||||  
|CREDENTIAL|???||WITH Credential wird nur unterstützt, wenn die Option Backup to URL zum Sichern im Azure BLOB Storage-Dienst verwendet wird.|  
|DIFFERENTIAL|???|||  
|COPY_ONLY|???|||  
|COMPRESSION&#124;NO_COMPRESSION|???|||  
|DESCRIPTION|???|||  
|NAME|???|||  
|EXPIREDATE &#124; RETAINDAYS|???|||  
|NOINIT &#124; INIT|???||Wenn diese Option verwendet wird, wird sie ignoriert.<br /><br /> Das Anfügen an BLOBs ist nicht möglich. Verwenden Sie zum Überschreiben einer Sicherung das FORMAT-Argument.|  
|NOSKIP &#124; SKIP|???|||  
|NOFORMAT &#124; FORMAT|???||Wenn diese Option verwendet wird, wird sie ignoriert.<br /><br /> Eine Sicherung, die auf ein vorhandenes BLOB geschrieben wird, ist nur erfolgreich, wenn WITH FORMAT angegeben wird. Das vorhandene BLOB wird bei Angabe von WITH FORMAT überschrieben.|  
|MEDIADESCRIPTION|???|||  
|MEDIANAME|???|||  
|BLOCKSIZE|???|||  
|BUFFERCOUNT|???|||  
|MAXTRANSFERSIZE|???|||  
|NO_CHECKSUM &#124; CHECKSUM|???|||  
|STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR|???|||  
|STATS|???|||  
|REWIND &#124; NOREWIND|???|||  
|UNLOAD &#124; NOUNLOAD|???|||  
|NORECOVERY &#124; STANDBY|???|||  
|NO_TRUNCATE|???|||  
  
 Weitere Informationen zu BACKUP-Argumenten finden Sie unter [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
### <a name="support-for-restore-arguments"></a>Unterstützung für RESTORE-Argumente  
  
|||||  
|-|-|-|-|  
|Argument|Supported|Ausnahmen|Kommentare|  
|DATABASE|???|||  
|LOG|???|||  
|FROM (URL)|???||Das FROM URL-Argument wird verwendet, um den URL-Pfad der Sicherungsdatei anzugeben.|  
|**WITH Options:**||||  
|CREDENTIAL|???||WITH Credential wird nur unterstützt, wenn die Option Restore from URL für die Wiederherstellung aus Azure BLOB Storage-Dienst verwendet wird.|  
|PARTIAL|???|||  
|RECOVERY &#124; NORECOVERY &#124; STANDBY|???|||  
|LOADHISTORY|???|||  
|MOVE|???|||  
|REPLACE|???|||  
|RESTART|???|||  
|RESTRICTED_USER|???|||  
|FILE|???|||  
|PASSWORD|???|||  
|MEDIANAME|???|||  
|MEDIAPASSWORD|???|||  
|BLOCKSIZE|???|||  
|BUFFERCOUNT|???|||  
|MAXTRANSFERSIZE|???|||  
|CHECKSUM &#124; NO_CHECKSUM|???|||  
|STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR|???|||  
|FILESTREAM|???|||  
|STATS|???|||  
|REWIND &#124; NOREWIND|???|||  
|UNLOAD &#124; NOUNLOAD|???|||  
|KEEP_REPLICATION|???|||  
|KEEP_CDC|???|||  
|ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER|???|||  
|STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK|???|||  
  
 Weitere Informationen zu RESTORE-Argumenten finden Sie unter [RESTORE-Argumente &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
##  <a name="BackupTaskSSMS"></a>Verwenden des Sicherungs Tasks in SQL Server Management Studio  
 Der Sicherungs Task in SQL Server Management Studio wurde verbessert, um URL als eine der Ziel Optionen und andere unterstützende Objekte einzuschließen, die für die Sicherung im Azure-Speicher wie die SQL-Anmelde Informationen erforderlich sind.  
  
 In den folgenden Schritten werden die Änderungen beschrieben, die am Task Datenbank sichern vorgenommen wurden, um die Sicherung im Azure-Speicher zu ermöglichen:  
  
1.  Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der SQL Server-Instanz her.  Wählen Sie eine Datenbank aus, die Sie sichern möchten, klicken Sie mit der rechten Maustaste auf **Tasks**, und wählen Sie **sichern aus.** Dadurch wird das Dialogfeld Datenbank sichern geöffnet.  
  
2.  Auf der Seite Allgemein wird die Option **URL** verwendet, um eine Sicherung im Azure-Speicher zu erstellen. Wenn Sie diese Option auswählen, werden weitere Optionen auf dieser Seite aktiviert:  
  
    1.  **Dateiname:** Name der Sicherungsdatei.  
  
    2.  **SQL-Anmelde Informationen:** Sie können entweder einen vorhandenen SQL Server Anmelde Informationen angeben oder einen neuen erstellen, indem Sie auf das Feld neben dem Feld SQL-Anmelde Informationen **Erstellen** klicken.  
  
        > [!IMPORTANT]  
        >  Das Dialogfeld, das beim Klicken auf **Erstellen** geöffnet wird, erfordert ein Verwaltungszertifikat oder das Veröffentlichungsprofil für das Abonnement. SQL Server unterstützt derzeit die Version 2.0 des Veröffentlichungsprofils. Weitere Informationen zum Herunterladen der unterstützten Version des Veröffentlichungsprofils finden Sie unter [Herunterladen des Veröffentlichungsprofils 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
        >   
        >  Wenn Sie keinen Zugriff auf das Verwaltungszertifikat oder Veröffentlichungsprofil haben, können Sie SQL-Anmeldeinformationen erstellen, indem Sie den Namen des Speicherkontos und die Informationen zum Zugriffsschlüssel mithilfe von Transact-SQL oder SQL Server Management Studio angeben. Der Beispielcode im Abschnitt [Erstellen von Anmeldeinformationen](#credential) veranschaulicht das Erstellen von Anmeldeinformationen mithilfe von Transact-SQL. Alternativ können Sie auf der Datenbank-Engine-Instanz in SQL Server Management Studio mit der rechten Maustaste auf **Sicherheit**klicken und **Neu**sowie **Anmeldeinformationen**auswählen. Geben Sie im Feld **Identität** den Namen des Speicherkontos und im Feld **Kennwort** den Zugriffsschlüssel an.  
  
    3.  **Azure-Speichercontainer:** Der Name des Azure-Speicher Containers, in dem die Sicherungsdateien gespeichert werden sollen.  
  
    4.  **URL-Präfix:** Diese wird automatisch mit den Informationen erstellt, die in den in den vorherigen Schritten beschriebenen Feldern angegeben sind. Wenn Sie diesen Wert manuell bearbeiten, stellen Sie sicher, dass er mit den anderen Informationen übereinstimmt, die Sie zuvor bereitgestellt haben. Wenn Sie beispielsweise die Speicher-URL ändern, sollten Sie sicherstellen, dass die SQL-Anmeldeinformationen für die Authentifizierung beim gleichen Speicherkonto festgelegt wurden.  
  
 Wenn Sie eine URL als Ziel auswählen, sind bestimmte Optionen auf der Seite **Medienoptionen** deaktiviert.  Die folgenden Themen enthalten weitere Informationen zum Dialogfeld Datenbank sichern:  
  
 [Datenbank sichern &#40;Seite Allgemein&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [Datenbank sichern &#40;Seite 'Medienoptionen'&#41;](back-up-database-media-options-page.md)  
  
 [Datenbank sichern &#40;Seite 'Sicherungsoptionen'&#41;](back-up-database-backup-options-page.md)  
  
 [Erstellen von Anmeldeinformationen – Authentifizieren beim Azure-Speicher](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="MaintenanceWiz"></a> SQL Server-Sicherung über URLs mithilfe des Wartungsplanungs-Assistenten  
 Ähnlich wie beim zuvor beschriebenen Sicherungs Task wurde der Wartungsplanungs-Assistent in SQL Server Management Studio erweitert, um die **URL** als eine der Ziel Optionen und andere unterstützende Objekte einzuschließen, die für die Sicherung im Azure-Speicher wie SQL benötigt werden. Anmelde Informationen. Weitere Informationen finden Sie unter der **Definieren von Sicherungstasks** im Abschnitt [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).  
  
##  <a name="RestoreSSMS"></a>Wiederherstellen aus Azure Storage mithilfe von SQL Server Management Studio  
 Wenn Sie eine Datenbank wiederherstellen, wird **URL** als Gerät für die Wiederherstellung eingeschlossen. Die folgenden Schritte beschreiben die Änderungen am Wiederherstellungs Task, um die Wiederherstellung aus Azure Storage zuzulassen:  
  
1.  Wenn Sie in SQL Server Management Studio auf der Seite **Allgemein** des Wiederherstellungstasks die Option **Geräte** auswählen, wird das Dialogfeld **Sicherungsmedien auswählen** geöffnet, das **URL** als Sicherungsmediumtyp enthält.  
  
2.  Wenn Sie **URL** auswählen und auf **Hinzufügen**klicken, wird das Dialogfeld **Mit Azure-Speicher verbinden** geöffnet. Geben Sie die SQL-Anmelde Informationen für die Authentifizierung beim Azure-Speicher an.  
  
3.  SQL Server dann mithilfe der angegebenen SQL-Anmelde Informationen eine Verbindung mit dem Azure-Speicher her und öffnet das Dialogfeld **Sicherungsdatei in Azure suchen** . Die Sicherungsdateien, die sich im Arbeitsspeicher befinden, werden auf dieser Seite angezeigt. Wählen Sie die Datei aus, die Sie zum Wiederherstellen verwenden möchten, und klicken Sie auf **OK**. So rufen Sie erneut in das Dialogfeld **Sicherungsmedien auswählen** auf. Wenn Sie in diesem Dialogfeld auf **OK** klicken, wird das Hauptdialogfeld **Wiederherstellen** aufgerufen, in dem Sie die Wiederherstellung abschließen können.  Weitere Informationen finden Sie in den folgenden Themen:  
  
     [Datenbank wiederherstellen &#40;Seite „Allgemein“&#41;](restore-database-general-page.md)  
  
     [Datenbank wiederherstellen &#40;Seite Dateien&#41;](restore-database-files-page.md)  
  
     [Datenbank wiederherstellen &#40;Seite Optionen&#41;](restore-database-options-page.md)  
  
##  <a name="Examples"></a> Codebeispiele  
 Dieser Abschnitt enthält die folgenden Beispiele.  
  
-   [Erstellen von Anmeldeinformationen](#credential)  
  
-   [Sichern einer vollständigen Datenbank](#complete)  
  
-   [Sichern der Datenbank und des Protokolls](#databaselog)  
  
-   [Erstellen einer vollständigen Datei Sicherung der primären Datei Gruppe](#filebackup)  
  
-   [Erstellen einer differenziellen Datei Sicherung der primären Dateigruppen](#differential)  
  
-   [Wiederherstellen einer Datenbank und Verschieben von Dateien](#restoredbwithmove)  
  
-   [Wiederherstellen eines bestimmten Zeitpunkts mithilfe von STOPAT](#PITR)  
  
###  <a name="credential"></a> Erstellen von Anmeldeinformationen  
 Im folgenden Beispiel werden Anmelde Informationen erstellt, in denen die Azure Storage Authentifizierungsinformationen gespeichert werden.  
  
1.  **Tsql**  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key>' ;  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
    string secret = "<storage access key>";  
  
    // Create a Credential  
    string credentialName = "mycredential";  
    Credential credential = new Credential(server, credentialName);  
    credential.Create(identity, secret);  
    ```  
  
3.  **PowerShell**  
  
    ```  
    # create variables  
    $storageAccount = "mystorageaccount"  
    $storageKey = "<storage access key>"  
    $secureString = convertto-securestring $storageKey  -asplaintext -force  
    $credentialName = "mycredential"  
  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # Create a credential  
     New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString  
  
    ```  
  
###  <a name="complete"></a>Sichern einer kompletten Datenbank  
 Im folgenden Beispiel wird die AdventureWorks2012-Datenbank im Azure-BLOB-Speicherdienst gesichert.  
  
1.  **Tsql**  
  
    ```  
    BACKUP DATABASE AdventureWorks2012   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
          WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
    GO  
  
    ```  
  
1.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
    ```  
  
2.  **PowerShell**  
  
    ```  
    # create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"   
    # for default instance, the $srvpath varilable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance  
    CD $srvPath   
    $backupFile = $backupUrlContainer + "AdventureWorks2012" +  ".bak"  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On  
  
    ```  
  
###  <a name="databaselog"></a>Sichern der Datenbank und des Protokolls  
 Im folgenden Beispiel wird die AdventureWorks2012-Beispieldatenbank gesichert, in der standardmäßig das einfache Wiederherstellungsmodell verwendet wird. Zur Unterstützung von Protokollsicherungen wird die AdventureWorks2012-Datenbank geändert, sodass sie das vollständige Wiederherstellungsmodell verwendet. Im Beispiel wird dann eine vollständige Datenbanksicherung im Azure-Blob erstellt, und nach einem Zeitraum der Update Aktivität wird das Protokoll gesichert. In diesem Beispiel wird für eine Sicherungsdatei ein Name mit einem Datums-/Zeitstempel erstellt.  
  
1.  **Tsql**  
  
    ```  
    -- To permit log backups, before the full database backup, modify the database   
    -- to use the full recovery model.  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012  
       SET RECOVERY FULL;  
    GO  
  
    -- Back up the full AdventureWorks2012 database.  
           -- First create a file name for the backup file with DateTime stamp  
  
    DECLARE @Full_Filename AS VARCHAR (300);  
    SET @Full_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Full_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.bak';   
    --Back up Adventureworks2012 database  
  
    BACKUP DATABASE AdventureWorks2012  
    TO URL =  @Full_Filename  
    WITH CREDENTIAL = 'mycredential';  
    ,COMPRESSION  
    GO  
    -- Back up the AdventureWorks2012 log.  
    DECLARE @Log_Filename AS VARCHAR (300);  
    SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
    BACKUP LOG AdventureWorks2012  
     TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,COMPRESSION;  
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url for data backup  
    string urlDataBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Data-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Database to Url  
    Backup backupData = new Backup();  
    backupData.CredentialName = credentialName;  
    backupData.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backupData.Devices.AddDevice(urlDataBackup, DeviceType.Url);  
    backupData.SqlBackup(server);  
  
    // Generate Unique Url for data backup  
    string urlLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Log-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Database Log to Url  
    Backup backupLog = new Backup();  
    backupLog.CredentialName = credentialName;  
    backupLog.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backupLog.Devices.AddDevice(urlLogBackup, DeviceType.Url);  
    backupLog.Action = BackupActionType.Log;  
    backupLog.SqlBackup(server);  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to theSQL Server Instance  
  
    CD $srvPath   
    #Create a unique file name for the full database backup  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    #Backup Database to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Database    
  
    #Create a unique file name for log backup  
  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup Log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Log  
  
    ```  
  
###  <a name="filebackup"></a>Erstellen einer vollständigen Datei Sicherung der primären Datei Gruppe  
 Im folgenden Beispiel wird eine vollständige Dateisicherung der primären Dateigruppe erstellt.  
  
1.  **Tsql**  
  
    ```  
    --Back up the files in Primary:  
    BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bck",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Action = BackupActionType.Files;  
    backup.DatabaseFileGroups.Add("PRIMARY");  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to the SQL Server Instance  
  
    CD $srvPath   
    #Create a unique file name for the file backup  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bck"  
  
    #Backup Primary File Group to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary  
  
    ```  
  
###  <a name="differential"></a>Erstellen einer differenziellen Datei Sicherung der primären Datei Gruppe  
 Im folgenden Beispiel wird eine differenzielle Dateisicherung der primären Dateigruppe erstellt.  
  
1.  **Tsql**  
  
    ```  
    --Back up the files in Primary:  
    BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012filesdiff.bck'  
       WITH   
          CREDENTIAL = 'mycredential'  
          ,COMPRESSION  
      ,DIFFERENTIAL;  
    GO  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Action = BackupActionType.Files;  
    backup.DatabaseFileGroups.Add("PRIMARY");  
    backup.Incremental = true;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance  
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    #Create a differential backup of the primary filegroup  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary -Incremental  
  
    ```  
  
###  <a name="restoredbwithmove"></a>Wiederherstellen einer Datenbank und Verschieben von Dateien  
 Zum Wiederherstellen einer vollständigen Datenbanksicherung und Verschieben der wiederhergestellten Datenbank in das Verzeichnis C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data führen Sie die folgenden Schritte aus.  
  
1.  **Tsql**  
  
    ```  
    -- Backup the tail of the log first  
  
    DECLARE @Log_Filename AS VARCHAR (300);  
    SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
    BACKUP LOG AdventureWorks2012  
     TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,NORECOVERY;  
    GO  
  
    RESTORE DATABASE AdventureWorks2012 FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'  
    WITH CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,MOVE 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,STATS = 5  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    // Generate Unique Url for tail log backup  
    string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Tail Log to Url  
    Backup backupTailLog = new Backup();  
    backupTailLog.CredentialName = credentialName;  
    backupTailLog.Database = dbName;  
    backupTailLog.Action = BackupActionType.Log;  
    backupTailLog.NoRecovery = true;  
    backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
    backupTailLog.SqlBackup(server);  
  
    // Restore a database and move files  
    string newDataFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
    string newLogFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
    Restore restore = new Restore();  
    restore.CredentialName = credentialName;  
    restore.Database = dbName;  
    restore.ReplaceDatabase = true;  
    restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
    restore.RelocateFiles.Add(new RelocateFile(dbName+ "_Log", newLogFilePath));  
    restore.SqlRestore(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTNACENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance   
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    # Full database backup to URL  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On      
  
    #Create a unique file name for the tail log backup  
    $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup tail log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery    
  
    # Restore Database and move files  
  
    $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
    $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath)  
  
    ```  
  
###  <a name="PITR"></a> Wiederherstellen eines bestimmten Zeitpunkts mithilfe von STOPAT  
 Im folgenden Beispiel wird der Zustand einer Datenbank zu einem bestimmten Zeitpunkt wiederhergestellt und ein Wiederherstellungsvorgang veranschaulicht.  
  
1.  **Tsql**  
  
    ```  
    RESTORE DATABASE AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
    WITH   
     CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,Move 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,NORECOVERY  
    --,REPLACE  
    ,STATS = 5;  
    GO   
  
    RESTORE LOG AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.trn'   
    WITH CREDENTIAL = 'mycredential'  
    ,RECOVERY   
    ,STOPAT = 'Oct 23, 2012 5:00 PM'   
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    // Generate Unique Url for Tail Log backup  
    string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Tail Log to Url  
    Backup backupTailLog = new Backup();  
    backupTailLog.CredentialName = credentialName;  
    backupTailLog.Database = dbName;  
    backupTailLog.Action = BackupActionType.Log;  
    backupTailLog.NoRecovery = true;  
    backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
    backupTailLog.SqlBackup(server);  
  
    // Restore a database and move files  
    string newDataFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
    string newLogFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
    Restore restore = new Restore();  
    restore.CredentialName = credentialName;  
    restore.Database = dbName;  
    restore.ReplaceDatabase = true;  
    restore.NoRecovery = true;  
    restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
    restore.RelocateFiles.Add(new RelocateFile(dbName + "_Log", newLogFilePath));  
    restore.SqlRestore(server);  
  
    // Restore transaction Log with stop at   
    Restore restoreLog = new Restore();  
    restoreLog.CredentialName = credentialName;  
    restoreLog.Database = dbName;  
    restoreLog.Action = RestoreActionType.Log;  
    restoreLog.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restoreLog.ToPointInTime = DateTime.Now.ToString();   
    restoreLog.SqlRestore(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # Navigate to SQL Server Instance Directory  
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    # Full database backup to URL  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On     
  
    #Create a unique file name for the tail log backup  
    $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup tail log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery     
  
    # Restore Database and move files  
  
    $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
    $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath) -NoRecovery    
  
    # Restore Transaction log with Stop At:  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backuplogFile  -ToPointInTime (Get-Date).ToString()  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Tutorial: SQL Server sichern und Wiederherstellen in Azure BLOB Storage Dienst](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
  
