---
title: SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
caps.latest.revision: 20
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f2c7a2cc478659dc3ba50a650a15168b37644619
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277076"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung
  In diesem Thema werden bewährte Methoden und Tipps zur Problembehandlung beschrieben, die sich auf SQL Server-Sicherungs- und Wiederherstellungsvorgänge im Windows Azure-BLOB-Dienst beziehen.  
  
 Weitere Informationen zur Verwendung des Windows Azure-BLOB-Speicherdiensts für SQL Server-Sicherungs- oder -Wiederherstellungsvorgänge finden Sie unter:  
  
-   [SQL Server-Sicherung und -Wiederherstellung mit dem Microsoft Azure Storage-Dienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [Lernprogramm: SQL Server-Sicherung und -Wiederherstellung im Windows Azure-BLOB-Speicherdienst](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>Verwalten von Sicherungen  
 Die folgende Liste enthält allgemeine Empfehlungen zur Verwaltung von Sicherungen:  
  
-   Für jede Sicherung sollte ein eindeutiger Dateiname verwendet werden, um zu verhindern, dass BLOBs versehentlich überschrieben werden.  
  
-   Beim Erstellen eines Containers wird empfohlen, die Zugriffsebene auf **Privat**festzulegen, sodass der Lese- oder Schreibzugriff auf Blobs im Container nur Benutzern oder Konten mit den erforderlichen Authentifizierungsinformationen gestattet ist.  
  
-   Um Übertragungskosten zwischen Regionen zu vermeiden, verwenden Sie für SQL Server-Datenbanken auf einer SQL Server-Instanz, die auf einem virtuellen Windows Azure-Computer ausgeführt wird, ein Speicherkonto, das derselben Region angehört wie das Speicherkonto des virtuellen Computers. Wenn Sie innerhalb einer Region bleiben, erzielen Sie darüber hinaus optimale Leistung bei Sicherungs- und Wiederherstellungsvorgängen.  
  
-   Eine fehlerhafte Sicherungsaktivität kann dazu führen, dass eine Sicherungsdatei unbrauchbar wird. Es wird empfohlen, regelmäßig nach fehlerhaften Sicherungen zu suchen und die BLOB-Dateien zu löschen. Weitere Informationen hierzu finden Sie unter [Löschen von Sicherungsblobdateien aktiver Lease](deleting-backup-blob-files-with-active-leases.md).  
  
-   Wenn Sie die Sicherung mit der `WITH COMPRESSION`-Option durchführen, können Sie die Speicherkosten und Speichertransaktionskosten minimieren. Darüber hinaus verkürzt die Option die Dauer des Sicherungsvorgangs.  
  
## <a name="handling-large-files"></a>Behandlung großer Dateien  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungsvorgänge verwenden mehrere Threads, um die Datenübertragung an die Windows Azure-BLOB-Speicherdienste zu optimieren.  Die Leistung hängt jedoch von verschiedenen Faktoren ab wie der Bandbreite des unabhängigen Softwareherstellers (ISV) und der Größe der Datenbank. Wenn Sie beabsichtigen, große Datenbanken oder Dateigruppen von einer lokalen SQL Server-Datenbank zu sichern, sollten Sie zunächst den Durchsatz testen. [Windows Azure-Speicher SLA](http://go.microsoft.com/fwlink/?LinkId=271619) bietet maximale verarbeitungsleistung für Blobs, die Sie als Ausgangspunkt verwenden können.  
  
-   Die Verwendung der im Abschnitt **Verwalten von Sicherungen** empfohlenen `WITH COMPRESSION`-Option ist besonders beim Sichern umfangreicher Dateien von Bedeutung.  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>Problembehandlung bei Sicherungs- oder Wiederherstellungsvorgängen über URLs  
 Im Folgenden finden Sie einige schnelle Lösungen zur Behandlung von Sicherungs- und Wiederherstellungsfehlern im Windows Azure-BLOB-Speicherdienst.  
  
 Um Fehler aufgrund nicht unterstützte Optionen oder Einschränkungen zu vermeiden, überprüfen Sie die Liste der Einschränkungen und Unterstützung für die Informationen zum SICHERUNGS- und Befehle in der [SQL Server-Sicherung und-Wiederherstellung mit dem Windows Azure-Blob-Speicherdienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) Artikel.  
  
 **Authentifizierungsfehler:**  
  
-   WITH CREDENTIAL ist eine neue Option, die für Sicherungs- oder Wiederherstellungsvorgänge im Windows Azure-BLOB-Speicherdienst erforderlich ist. In Zusammenhang mit Anmeldeinformationen können folgende Fehler auftreten:  
  
     Im angegebenen Anmeldeinformationen die `BACKUP` oder `RESTORE` Befehl ist nicht vorhanden. Um dieses Problem zu vermeiden, können Sie T-SQL-Anweisungen zum Erstellen von Anmeldeinformationen einschließen, falls in der BACKUP-Anweisung keine Anmeldeinformationen enthalten sind. Beachten Sie das folgende Anwendungsbeispiel:  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   Die Anmeldeinformationen sind zwar vorhanden, aber das Anmeldekonto zum Ausführen des Sicherungsbefehls verfügt über keine Berechtigung für den Zugriff auf die Anmeldeinformationen. Verwenden Sie ein Anmeldekonto aus der **db_backupoperator** -Rolle mit Berechtigungen für **Beliebige Anmeldeinformationen ändern** .  
  
-   Überprüfen Sie den Namen des Speicherkontos und die Schlüsselwerte. Die in den Anmeldeinformationen gespeicherten Informationen müssen den Eigenschaftswerten des Windows Azure-Speicherkontos entsprechen, das Sie für Sicherungs- und Wiederherstellungsvorgänge verwenden.  
  
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
  
    -   Sie finden die Informationen auch, indem Sie im Windows-Ereignisprotokoll in den Anwendungsprotokollen nach dem Namen "SQLBackupToUrl" suchen.  
  
-   Bei der Wiederherstellung von einer komprimierten Sicherung kann eine Fehlermeldung mit etwa folgendem Wortlaut angezeigt werden:  
  
    -   **SqlException 3284 aufgetreten. Schweregrad: 16; Status: 5**  
        **Nachricht Dateimarkierung für Gerät "https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak' ist nicht ausgerichtet. Geben Sie die RESTORE-Anweisung mit derselben Blockgröße, die zum Erstellen des Sicherungssatzes verwendet wurde, erneut aus: '65536' sieht wie ein möglicher Wert aus.**  
  
         Um diesen Fehler zu beheben, übergeben Sie die `BACKUP`-Anweisung erneut mit `BLOCKSIZE = 65536`.  
  
-   Sicherungsfehler aufgrund von BLOBs, die über eine aktive Leasedauer verfügen: Fehlerhafte Sicherungsaktivitäten können dazu führen, dass BLOBs eine aktive Leasedauer aufweisen.  
  
     Wenn die BACKUP-Anweisung erneut ausgeführt wird, kann ein Sicherungsvorgang einen Fehler mit etwa folgendem Wortlaut verursachen:  
  
     **Bei einer URL-Sicherung wurde eine Ausnahme vom Remoteendpunkt empfangen. Ausnahmemeldung: Der Remoteserver hat einen Fehler zurückgegeben: (412) Derzeit weist das Blob eine Lease auf, obwohl in der Anforderung keine Lease-ID angegeben wurde**.  
  
     Wenn versucht wird, eine RESTORE-Anweisung für eine BLOB-Sicherungsdatei mit aktiver Leasedauer auszuführen, wird eine Fehlermeldung mit etwa folgendem Wortlaut angezeigt:  
  
     **Ausnahmemeldung: Der Remoteserver hat einen Fehler zurückgegeben: (409) Konflikt...**  
  
     Wenn dieser Fehler auftritt, müssen die BLOB-Dateien gelöscht werden. Weitere Informationen zu diesem Szenario und Lösungsvorschläge finden Sie unter [Löschen von Sicherungsblobdateien mit aktiver Lease](deleting-backup-blob-files-with-active-leases.md).  
  
## <a name="proxy-errors"></a>Proxyfehler  
 Wenn Sie über Proxyserver auf das Internet zugreifen, können folgende Probleme auftreten:  
  
 **Durch Proxyserver gedrosselte Verbindungen:**  
  
 Proxyserver können über Einstellungen verfügen, die die Anzahl der Verbindungen pro Minute begrenzen. Der URL-Sicherungsprozess ist ein Multithreadprozess und kann diese Begrenzung folglich überschreiten. In diesem Fall wird die Verbindung vom Proxyserver abgebrochen. Um das Problem zu beheben, ändern Sie die Proxyeinstellungen, damit der Proxy von SQL Server nicht verwendet wird.   Im Folgenden einige Beispiele für Fehlertypen oder -meldungen, die im Fehlerprotokoll angezeigt werden können:  
  
-   Schreiben Sie auf "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak" Fehler: URL-Sicherung wurde eine Ausnahme vom Remoteendpunkt empfangen. Ausnahmemeldung: Von der Übertragungsverbindung können keine Daten gelesen werden: Die Verbindung wurde geschlossen.  
  
-   Nicht behebbarer E/A-Fehler für die Datei http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: Error could not be gathered from Remote Endpoint. (Fehler konnte am Endpunkt nicht erfasst werden.)  
  
     Meldung 3013, Ebene 16, Status 1, Zeile 2  
  
     BACKUP DATABASE wird fehlerbedingt beendet.  
  
-   Backupiorequest::: Schreibfehler auf Sicherungsmedium http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak". Betriebssystemfehler: Bei einer URL-Sicherung wurde eine Ausnahme vom Remoteendpunkt empfangen. Ausnahmemeldung: Von der Übertragungsverbindung können keine Daten gelesen werden: Die Verbindung wurde geschlossen.  
  
 Wenn Sie die ausführliche Protokollierung mit Ablaufverfolgungsflag 3051 aktivieren, können auch folgende Meldungen in den Protokollen angezeigt werden:  
  
 HTTP-Statuscode 502, HTTP-Statusmeldung: Proxyfehler (Die Anzahl der HTTP-Anforderungen pro Minute hat das konfigurierte Limit überschritten. Wenden Sie sich an Ihren ISA Server-Administrator.  )  
  
 **Standardproxyeinstellungen wurden nicht abgerufen:**  
  
 In einigen Fällen werden die Standardeinstellungen nicht abgerufen, wodurch Proxyauthentifizierungsfehler wie der folgende verursacht werden: *Nicht behebbarer E/A-Fehler für die Datei http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: BACKUP TO URL hat eine Ausnahme vom Remoteendpunkt empfangen. Ausnahmemeldung: Der Remoteserver hat einen Fehler zurückgegeben: (407)* **Proxyauthentifizierung erforderlich**.  
  
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
  
2.  Speichern Sie die Konfigurationsdatei im Ordner Binn der SQL Server-Instanz. Beispielsweise, wenn SQL Server auf dem Laufwerk C des Computers installiert ist, setzen Sie die Konfigurationsdatei hier: *c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL12.\< Instanzname > \MSSQL\Binn*.  
  
## <a name="troubleshooting-sql-server-managed-backup-to-windows-azure"></a>Problembehandlung für SQL Server Managed Backup für Windows Azure  
 Da SQL Server Managed Backup auf der URL-Sicherung aufbaut, gelten die in den vorherigen Abschnitten aufgeführten Tipps zur Fehlerbehebung für Datenbanken oder Instanzen, für die SQL Server Managed Backup verwendet wird.  Informationen zur Problembehandlung bei SQL Server Managed Backup für Windows Azure wird ausführlich beschrieben [Problembehandlung bei SQL Server Managed Backup für Windows Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Wiederherstellen von in Microsoft Azure gespeicherten Sicherungen](restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
