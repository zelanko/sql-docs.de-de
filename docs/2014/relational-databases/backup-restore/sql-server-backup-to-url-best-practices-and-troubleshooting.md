---
title: SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ac34c95e7ee4dc6f57ef7d8806a7db1bb981a944
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70175962"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung
  Dieses Thema enthält bewährte Methoden und Tipps zur Problembehandlung für SQL Server Sicherung und Wiederherstellung im Azure-BLOB-Dienst.  
  
 Weitere Informationen zum Verwenden des Azure BLOB Storage-diensdienstanbieter für SQL Server Sicherungs-oder Wiederherstellungs Vorgänge finden Sie unter:  
  
-   [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [Tutorial: SQL Server sichern und Wiederherstellen in Azure BLOB Storage Dienst](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>Verwalten von Sicherungen  
 Die folgende Liste enthält allgemeine Empfehlungen zur Verwaltung von Sicherungen:  
  
-   Für jede Sicherung sollte ein eindeutiger Dateiname verwendet werden, um zu verhindern, dass BLOBs versehentlich überschrieben werden.  
  
-   Beim Erstellen eines Containers wird empfohlen, die Zugriffsebene auf **Privat**festzulegen, sodass der Lese- oder Schreibzugriff auf Blobs im Container nur Benutzern oder Konten mit den erforderlichen Authentifizierungsinformationen gestattet ist.  
  
-   Verwenden Sie für SQL Server-Datenbanken in einer Instanz von SQL Server, die auf einem virtuellen Azure-Computer ausgeführt wird, ein Speicherkonto in derselben Region wie der virtuelle Computer, um Datenübertragungskosten zwischen Regionen zu vermeiden. Wenn Sie innerhalb einer Region bleiben, erzielen Sie darüber hinaus optimale Leistung bei Sicherungs- und Wiederherstellungsvorgängen.  
  
-   Eine fehlerhafte Sicherungsaktivität kann dazu führen, dass eine Sicherungsdatei unbrauchbar wird. Es wird empfohlen, regelmäßig nach fehlerhaften Sicherungen zu suchen und die BLOB-Dateien zu löschen. Weitere Informationen hierzu finden Sie unter [Löschen von Sicherungsblobdateien aktiver Lease](deleting-backup-blob-files-with-active-leases.md).  
  
-   Wenn Sie die Sicherung mit der `WITH COMPRESSION`-Option durchführen, können Sie die Speicherkosten und Speichertransaktionskosten minimieren. Darüber hinaus verkürzt die Option die Dauer des Sicherungsvorgangs.  
  
## <a name="handling-large-files"></a>Behandlung großer Dateien  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherungs Vorgang verwendet mehrere Threads, um die Datenübertragung an Azure-BLOB-Speicherdienste zu optimieren.  Die Leistung hängt jedoch von verschiedenen Faktoren ab wie der Bandbreite des unabhängigen Softwareherstellers (ISV) und der Größe der Datenbank. Wenn Sie beabsichtigen, große Datenbanken oder Dateigruppen von einer lokalen SQL Server-Datenbank zu sichern, sollten Sie zunächst den Durchsatz testen. [Die Azure Storage-SLA](https://go.microsoft.com/fwlink/?LinkId=271619) hat maximale Verarbeitungszeiten für BLOB, die Sie in Erwägung ziehen können.  
  
-   Die Verwendung der im Abschnitt **Verwalten von Sicherungen** empfohlenen `WITH COMPRESSION`-Option ist besonders beim Sichern umfangreicher Dateien von Bedeutung.  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>Problembehandlung bei Sicherungs- oder Wiederherstellungsvorgängen über URLs  
 Im folgenden finden Sie einige schnelle Möglichkeiten zur Problembehandlung bei der Sicherung oder Wiederherstellung im Azure BLOB Storage-Dienst.  
  
 Um Fehler aufgrund von nicht unterstützten Optionen oder Einschränkungen zu vermeiden, überprüfen Sie die Liste der Einschränkungen und die Unterstützung für Sicherungs-und Wiederherstellungs Befehle im Artikel [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) .  
  
 **Authentifizierungsfehler:**  
  
-   WITH Credential ist eine neue Option, die zum Sichern oder Wiederherstellen aus dem Azure BLOB Storage-Dienst erforderlich ist. In Zusammenhang mit Anmeldeinformationen können folgende Fehler auftreten:  
  
     Die im `BACKUP`-Befehl oder `RESTORE`-Befehl angegebenen Anmeldeinformationen sind nicht vorhanden. Um dieses Problem zu vermeiden, können Sie T-SQL-Anweisungen zum Erstellen von Anmeldeinformationen einschließen, falls in der BACKUP-Anweisung keine Anmeldeinformationen enthalten sind. Beachten Sie das folgende Anwendungsbeispiel:  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   Die Anmeldeinformationen sind zwar vorhanden, aber das Anmeldekonto zum Ausführen des Sicherungsbefehls verfügt über keine Berechtigung für den Zugriff auf die Anmeldeinformationen. Verwenden Sie ein Anmeldekonto aus der **db_backupoperator** -Rolle mit Berechtigungen für **Beliebige Anmeldeinformationen ändern** .  
  
-   Überprüfen Sie den Namen des Speicherkontos und die Schlüsselwerte. Die in den Anmelde Informationen gespeicherten Informationen müssen den Eigenschafts Werten des Azure-Speicher Kontos entsprechen, das Sie in den Sicherungs-und Wiederherstellungs Vorgängen verwenden.  
  
 **Sicherungsfehler:**  
  
-   Parallele Sicherungen im selben Blob führen dazu, dass bei einer der Sicherungen die Meldung **Fehler beim Initialisieren** ausgegeben wird.  
  
-   Verwenden Sie die folgenden Fehlerprotokolle, die Ihnen die Problembehandlung bei Sicherungsfehlern erleichtern:  
  
    -   Legen Sie das Ablaufverfolgungsflag 3051 wie folgt fest, um die Protokollierung in einem bestimmten Fehlerprotokoll zu aktivieren:  
  
         BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log. Dabei entspricht \<action> einem der folgenden Schlüsselwörter:  
  
        -   `DB`  
  
        -   `FILELISTONLY`  
  
        -   `LABELONLY`  
  
        -   `HEADERONLY`  
  
        -   `VERIFYONLY`  
  
    -   Informationen finden Sie auch im Windows-Ereignisprotokoll unter Anwendungsprotokolle mit dem Namen "sqlbackuptourl".  
  
-   Bei der Wiederherstellung von einer komprimierten Sicherung kann eine Fehlermeldung mit etwa folgendem Wortlaut angezeigt werden:  
  
    -   **SqlException 3284 aufgetreten. Zunehmen 16-Status: 5**  
        **Die Nachrichten dateinmarkierung auf https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak dem Gerät "" ist nicht ausgerichtet. Wiederholen Sie die RESTORE-Anweisung mit derselben Blockgröße, die zum Erstellen des backaufgeregt verwendet wurde: "65536" sieht wie ein möglicher Wert aus.**  
  
         Um diesen Fehler zu beheben, übergeben Sie die `BACKUP`-Anweisung erneut mit `BLOCKSIZE = 65536`.  
  
-   Fehler während der Sicherung aufgrund von Blobs mit aktiver Lease: Eine fehlerhafte Sicherungsaktivität kann zu Blobs mit aktiven Leases führen.  
  
     Wenn die BACKUP-Anweisung erneut ausgeführt wird, kann ein Sicherungsvorgang einen Fehler mit etwa folgendem Wortlaut verursachen:  
  
     **Bei einer URL-Sicherung wurde eine Ausnahme vom Remoteendpunkt empfangen. Ausnahme Meldung: The remote server returned an error: (412) derzeit ist eine Lease für das BLOB vorhanden, und in der Anforderung**wurde keine Lease-ID angegeben.  
  
     Wenn versucht wird, eine RESTORE-Anweisung für eine BLOB-Sicherungsdatei mit aktiver Leasedauer auszuführen, wird eine Fehlermeldung mit etwa folgendem Wortlaut angezeigt:  
  
     **Ausnahme Meldung: The remote server returned an error: (409) Konflikt..**  
  
     Wenn dieser Fehler auftritt, müssen die BLOB-Dateien gelöscht werden. Weitere Informationen zu diesem Szenario und Lösungsvorschläge finden Sie unter [Löschen von Sicherungsblobdateien mit aktiver Lease](deleting-backup-blob-files-with-active-leases.md).  
  
## <a name="proxy-errors"></a>Proxyfehler  
 Wenn Sie über Proxyserver auf das Internet zugreifen, können folgende Probleme auftreten:  
  
 **Durch Proxyserver gedrosselte Verbindungen:**  
  
 Proxyserver können über Einstellungen verfügen, die die Anzahl der Verbindungen pro Minute begrenzen. Der URL-Sicherungsprozess ist ein Multithreadprozess und kann diese Begrenzung folglich überschreiten. In diesem Fall wird die Verbindung vom Proxyserver abgebrochen. Um das Problem zu beheben, ändern Sie die Proxyeinstellungen, damit der Proxy von SQL Server nicht verwendet wird.   Im Folgenden einige Beispiele für Fehlertypen oder -meldungen, die im Fehlerprotokoll angezeigt werden können:  
  
-   Fehler beim Schreiben http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak in "": Bei der URL-Sicherung wurde eine Ausnahme vom Remote Endpunkt empfangen. Ausnahme Meldung: Daten können nicht aus der Transport Verbindung gelesen werden: Die Verbindung wurde geschlossen.  
  
-   Nicht behebbarer E/A-Fehler für die Datei "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: " Error could not be gathered from Remote Endpoint. (Fehler konnte am Endpunkt nicht erfasst werden.)  
  
     Meldung 3013, Ebene 16, Status 1, Zeile 2  
  
     BACKUP DATABASE wird fehlerbedingt beendet.  
  
-   Backupiorequest:: reportioerror: Schreibfehler auf dem Sicherungsmedium http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak "". Betriebssystemfehler: Bei einer URL-Sicherung wurde eine Ausnahme vom Remoteendpunkt empfangen. Ausnahme Meldung: Daten können nicht aus der Transport Verbindung gelesen werden: Die Verbindung wurde geschlossen.  
  
 Wenn Sie die ausführliche Protokollierung mit Ablaufverfolgungsflag 3051 aktivieren, können auch folgende Meldungen in den Protokollen angezeigt werden:  
  
 HTTP-Statuscode 502, HTTP-Statusmeldung: Proxyfehler (Die Anzahl der HTTP-Anforderungen pro Minute hat das konfigurierte Limit überschritten. Wenden Sie sich an Ihren ISA Server-Administrator.  )  
  
 **Standardproxyeinstellungen wurden nicht abgerufen:**  
  
 In einigen Fällen werden die Standardeinstellungen nicht abgerufen, wodurch Proxyauthentifizierungsfehler wie der folgende verursacht werden: *Nicht behebbarer E/A-Fehler für die Datei "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: " BACKUP TO URL hat eine Ausnahme vom Remoteendpunkt empfangen. Ausnahme Meldung: The remote server returned an error: (407) **Proxy Authentifizierung erforderlich.***  
  
 Um dieses Problem zu beheben, erstellen Sie mithilfe folgender Schritte eine Konfigurationsdatei, durch die beim URL-Sicherungsprozess die Standardproxyeinstellungen verwendet werden können:  
  
1.  Erstellen Sie eine Konfigurationsdatei mit dem Namen BackuptoURL.exe.config und folgender XML:  
  
    ```  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
  
    ```  
  
2.  Speichern Sie die Konfigurationsdatei im Ordner Binn der SQL Server-Instanz. Wenn beispielsweise meine SQL Server auf dem Laufwerk C des Computers installiert ist, platzieren Sie die Konfigurationsdatei hier: *C:\Programme\Microsoft SQL server\mssql12. \<InstanceName > \MSSQL\Binn*.  
  
## <a name="troubleshooting-sql-server-managed-backup-to-azure"></a>Problembehandlung SQL Server verwalteten Sicherung in Azure  
 Da SQL Server Managed Backup auf der URL-Sicherung aufbaut, gelten die in den vorherigen Abschnitten aufgeführten Tipps zur Fehlerbehebung für Datenbanken oder Instanzen, für die SQL Server Managed Backup verwendet wird.  Informationen zur Problembehandlung SQL Server verwalteten Sicherung in Azure finden Sie unter [Problembehandlung SQL Server verwaltete Sicherung in Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Wiederherstellen von in Azure gespeicherten Sicherungen](restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
