---
title: Sicherungsmedien (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tape backup devices, about tape backup devices
- backup devices [SQL Server]
- disk backup devices [SQL Server]
- database backups [SQL Server], backup devices
- logical devices [SQL Server]
- backup devices [SQL Server], about backup devices
- backing up [SQL Server], backup devices
- removable media [SQL Server]
- network shares [SQL Server]
- backups [SQL Server], backup devices
- tape backup devices
- physical devices [SQL Server]
- backing up databases [SQL Server], backup devices
- devices [SQL Server]
ms.assetid: 35a8e100-3ff2-4844-a5da-dd088c43cba4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 44cb3f6b8dd16eed44568051e1ef183c0ac8123a
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155047"
---
# <a name="backup-devices-sql-server"></a>Sicherungsmedien (SQL Server)
  Während eines Sicherungsvorgangs in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank werden die gesicherten Daten (die *Sicherung*) auf ein physisches Sicherungsmedium geschrieben. Dieses physische Sicherungsmedium wird initialisiert, wenn die erste Sicherung in einem Mediensatz darauf geschrieben wird. Die Sicherungen auf einem Satz von einem oder mehreren Sicherungsmedien bilden einen einzelnen Mediensatz.  
  
 **In diesem Thema:**  
  
-   [Begriffe und Definitionen](#TermsAndDefinitions)  
  
-   [Verwenden von Datenträger Sicherungsmedien](#DiskBackups)  
  
-   [Verwenden von Bandmedien](#TapeDevices)  
  
-   [Verwenden eines logischen Sicherungs Mediums](#LogicalBackupDevice)  
  
-   [Gespiegelte Sicherungsmedien Sätze](#MirroredMediaSets)  
  
-   [Archivieren von SQL Server Sicherungen](#Archiving)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="TermsAndDefinitions"></a> Begriffe und Definitionen  
 Sicherungsdatenträger  
 Eine Festplatte oder ein anderes Datenträgerspeichermedium, die bzw. das eine oder mehrere Sicherungsdateien enthält. Eine Sicherungsdatei ist eine reguläre Betriebssystemdatei.  
  
 Mediensatz  
 Eine geordnete Auflistung von Sicherungsmedien (Bänder oder Dateien auf Datenträgern), für die ein fester Typ sowie eine feste Anzahl von Sicherungsmedien verwendet wird. Weitere Informationen über Mediensätze finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
 Physisches Sicherungsmedium  
 Entweder ein Bandlaufwerk oder eine vom Betriebssystem bereitgestellte Datei auf dem Datenträger. Eine Sicherung kann auf 1 bis 64 Sicherungsmedien geschrieben werden. Wenn für eine Sicherung mehrere Sicherungsmedien benötigt werden, müssen diese ohne Ausnahme demselben Medientyp angehören (Datenträger oder Band).  
  
 SQL Server Sicherungen können auch zusätzlich zu einem Datenträger oder Band in den Azure-BLOB-Speicherdienst geschrieben werden.  
  
##  <a name="DiskBackups"></a>Verwenden von Datenträger Sicherungsmedien  
 **In diesem Abschnitt:**  
  
-   [Angeben einer Sicherungsdatei unter Verwendung des physischen namens (Transact-SQL)](#BackupFileUsingPhysicalName)  
  
-   [Angeben des Pfads für eine Datenträger Sicherungsdatei](#BackupFileDiskPath)  
  
-   [Sichern in eine Datei auf einer Netzwerkfreigabe](#NetworkShare)  
  
 Wenn sich eine Datenträgerdatei füllt, während bei einem Sicherungsvorgang dem Mediensatz eine Sicherung hinzugefügt wird, kann die Sicherungsvorgang nicht bis zum Ende ausgeführt werden. Die maximale Größe einer Sicherungsdatei wird durch den freien Speicherplatz auf dem Datenträgermedium bestimmt. Die geeignete Größe für ein Datenträgersicherungsmedium hängt daher von der Größe Ihrer Sicherungen ab.  
  
 Ein Datenträgersicherungsmedium kann ein einfacher Datenträger sein, z. B. ein ATA-Laufwerk. Alternativ kann auch ein im laufenden Betrieb austauschbares Datenträgerlaufwerk verwendet werden, das den Vorteil hat, dass Sie auf transparente Weise einen vollen Datenträger gegen einen leeren austauschen können. Ein Sicherungsdatenträger kann ein lokaler Datenträger auf dem Server oder ein als Netzwerkressource freigegebener Remotedatenträger sein. Informationen zum Verwenden eines Remotedatenträgers finden Sie unter [Sichern in eine Datei auf einer Netzwerkfreigabe](#NetworkShare)weiter unten in diesem Thema.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verwaltungstools bieten eine hohe Flexibilität beim Verwalten von Datenträgersicherungsmedien, da sie automatisch einen zeitgestempelten Dateinamen für die Datei auf dem Datenträger generieren.  
  
> [!IMPORTANT]  
>  Als Sicherungsdatenträger sollte ein anderer Datenträger als für die Datenbankdaten und Protokolldatenträger verwendet werden. Nur so kann sichergestellt werden, dass Sie auch dann auf die Sicherungen zugreifen können, wenn die Daten- oder Protokolldatenträger ausfallen.  
  
###  <a name="BackupFileUsingPhysicalName"></a>Angeben einer Sicherungsdatei unter Verwendung des physischen namens (Transact-SQL)  
 Die grundlegende [BACKUP](/sql/t-sql/statements/backup-transact-sql) -Syntax zum Angeben einer Sicherungsdatei mithilfe des Namens des physischen Mediums lautet wie folgt:  
  
 BACKUP DATABASE *Name der Datenbank*  
  
 TO DISK **=** { **'** _Name des physischen Sicherungsmediums_ **'**  |  **@** _physical_backup_device_name_var_ }  
  
 Zum Beispiel:  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';  
GO  
```  
  
 Die grundlegende Syntax zum Angeben eines physischen Datenträgermediums in einer [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) -Anweisung lautet:  
  
 RESTORE { DATABASE | LOG } *Name der Datenbank*  
  
 FROM DISK **=** { **'** _Name des physischen Sicherungsmediums_ **'**  |  **@** _physical_backup_device_name_var_ }  
  
 Ein auf ein Objekt angewendeter  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';   
```  
  
###  <a name="BackupFileDiskPath"></a>Angeben des Pfads für eine Datenträger Sicherungsdatei  
 Wenn Sie eine Sicherungsdatei angeben, sollten Sie den vollständigen Pfad und den Dateinamen angeben. Wenn Sie beim Sichern der Datei nur den Dateinamen oder einen relativen Pfad angeben, wird die Sicherungsdatei im Standardsicherungsverzeichnis gespeichert. Das Standardsicherungsverzeichnis lautet „C:\Programme\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup“, wobei mit *n* die Nummer der Serverinstanz angegeben wird. Für die Standardserverinstanz lautet das standardmäßige Sicherungsverzeichnis deshalb: C:\Programme\Microsoft SQL server\mssql12. MSSQLSERVER\MSSQL\Backup.  
  
 Für eine eindeutige Zuordnung (insbesondere in Skripts) empfiehlt sich die explizite Angabe des Pfads für das Sicherungsverzeichnis in allen DISK-Klauseln. Wenn Sie den Abfrage-Editor verwenden, ist dieser Aspekt weniger wichtig. In diesem Fall, wenn Sie sicherstellen können, dass sich die Sicherungsdatei im Standardsicherungsverzeichnis befindet, können Sie die Pfadangabe in der DISK-Klausel auslassen. Beispielsweise wird die `BACKUP` -Datenbank mithilfe der folgenden [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Anweisung im Standardsicherungsverzeichnis gesichert.  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'AdventureWorks2012.bak';  
GO  
```  
  
> [!NOTE]  
>  Der Standardspeicherort wird im **BackupDirectory** -Registrierungsschlüssel unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer**gespeichert.  
  
###  <a name="NetworkShare"></a>Sichern in eine Datei auf einer Netzwerkfreigabe  
 Damit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf eine Datei auf einem Remotedatenträger zugreifen kann, muss das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto Zugriff auf die Netzwerkfreigabe haben. Dazu gehören auch Berechtigungen, die erforderlich sind, damit Sicherungsvorgänge auf die Netzwerkfreigabe schreiben und Wiederherstellungsvorgänge die Sicherungsdaten auf der Netzwerkfreigabe lesen können. Die Verfügbarkeit von Netzlaufwerken und Berechtigungen hängt von dem Kontext ab, in dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst ausgeführt wird:  
  
-   Zum Sichern eines Netzlaufwerks, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Kontext eines Domänenbenutzerkontos ausgeführt wird, muss das freigegebene Laufwerk in der Sitzung, in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, als Netzlaufwerk zugeordnet sein. Wenn Sie Sqlservr.exe über die Befehlszeile starten, werden in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sämtliche Netzlaufwerke angezeigt, die Sie in Ihrer Anmeldesitzung zugeordnet haben.  
  
-   Wenn Sie Sqlservr.exe als Dienst ausführen, wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einer separaten Sitzung ausgeführt, die nicht mit Ihrer Anmeldesitzung in Zusammenhang steht. Die Sitzung, in der ein Dienst ausgeführt wird, kann über eigene zugeordnete Laufwerke verfügen (obwohl das normalerweise nicht der Fall ist).  
  
-   Sie können eine Verbindung mit dem Netzwerkdienstkonto herstellen, indem Sie statt eines Domänenbenutzers das Computerkonto verwenden. Damit Sicherungen von bestimmten Computern auf ein freigegebenes Laufwerk zulässig sind, müssen Sie den Computerkonten entsprechende Zugriffsberechtigungen erteilen. Solange der Sqlservr.exe-Prozess, der die Sicherung schreibt, Zugriff hat, spielt es keine Rolle, ob der Benutzer, der den BACKUP-Befehl sendet, ebenfalls Zugriff hat.  
  
    > [!IMPORTANT]  
    >  Da es bei Vorliegen von Netzwerkfehlern beim Sichern von Daten über ein Netzwerk zu Störungen kommen kann, sollten Sie bei Verwendung eines Remotedatenträgers den Sicherungsvorgang am Ende überprüfen. Weitere Informationen finden Sie unter [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).  
  
#### <a name="specifying-a-universal-naming-convention-unc-name"></a>Angeben eines UNC-Namen (Universal Naming Convention)  
 Zum Angeben einer Netzwerkfreigabe in einem Sicherungs- oder Wiederherstellungsbefehl sollten Sie den vollqualifizierten UNC-Namen der Datei für das Sicherungsmedium verwenden. Ein UNC-Name weist das Format **\\\\** _Systemname_ **\\** _ShareName_ **\\** _Path_ **\\** _FileName_.  
  
 Zum Beispiel:  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = '\\BackupSystem\BackupDisk1\AW_backups\AdventureWorksData.Bak';  
GO  
```  
  
##  <a name="TapeDevices"></a>Verwenden von Bandmedien  
  
> [!NOTE]  
>  Die Unterstützung für Bandsicherungsgeräte wird in zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.  
  
 **In diesem Abschnitt:**  
  
-   [Angeben eines Sicherungs Bands unter Verwendung des physischen namens (Transact-SQL)](#BackupTapeUsingPhysicalName)  
  
-   [Band spezifische Backup-und Restore-Optionen (Transact-SQL)](#TapeOptions)  
  
-   [Verwalten offener Bänder](#OpenTapes)  
  
 Zum Sichern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten auf Band ist mindestens ein Bandlaufwerk erforderlich, das vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Betriebssystem unterstützt wird. Verwenden Sie für diese Laufwerke nur die vom Hersteller des Laufwerks empfohlenen Bänder. Weitere Informationen zum Installieren eines Bandlaufwerks finden Sie in der Dokumentation zum Windows-Betriebssystem.  
  
 Wenn ein Bandlaufwerk verwendet wird, kann ein Sicherungsvorgang ein Band füllen und mit einem anderen Band fortfahren. Jedes Band enthält einen Medienheader. Das erste verwendete Medium wird als *Anfangsband*bezeichnet. Jedes darauf folgende Band wird als *Anschlussband* bezeichnet und verfügt über eine Mediensequenznummer (aufsteigend). Ein Mediensatz, der beispielsweise vier Bandmedien zugewiesen ist, enthält mindestens vier Anfangsbänder (und, bei Bedarf für die Datenbank vier weitere Reihen mit Anschlussbändern). Wenn Sie einen Sicherungssatz anfügen, müssen Sie das letzte Band in der Reihe einlegen. Wenn das letzte Band nicht eingelegt wurde, wird der Scanvorgang von [!INCLUDE[ssDE](../../includes/ssde-md.md)] bis zum Ende des eingelegten Bands fortgesetzt, woraufhin Sie das Band wechseln müssen. Legen Sie zu diesem Zeitpunkt das letzte Band ein.  
  
 Bandsicherungsmedien werden wie Datenträgermedien verwendet. Es gelten folgende Ausnahmen:  
  
-   Das Bandmedium muss physisch mit dem Computer verbunden sein, auf dem eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird. Das Sichern auf Remotebandmedien wird nicht unterstützt.  
  
-   Wenn ein Bandsicherungsmedium während des Sicherungsvorgangs gefüllt wird, jedoch noch weitere Daten geschrieben werden müssen, fordert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Einlegen eines neues Bands auf, und setzt danach den Sicherungsvorgang fort.  
  
###  <a name="BackupTapeUsingPhysicalName"></a>Angeben eines Sicherungs Bands unter Verwendung des physischen namens (Transact-SQL)  
 Die grundlegende [BACKUP](/sql/t-sql/statements/backup-transact-sql) -Syntax zum Angeben eines Sicherungsbands mithilfe des physischen Gerätenamens des Bandlaufwerks lautet wie folgt:  
  
 BACKUP { DATABASE | LOG } *Name der Datenbank*  
  
 TO TAPE **=** { **'** _Name des physischen Sicherungsmediums_ **'**  |  **@** _physical_backup_device_name_var_ }  
  
 Zum Beispiel:  
  
```  
BACKUP LOG AdventureWorks2012   
   TO TAPE = '\\.\tape0';  
GO  
```  
  
 Die grundlegende Syntax zum Angeben eines physischen Bandmediums in einer [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) -Anweisung lautet:  
  
 RESTORE { DATABASE | LOG } *Name der Datenbank*  
  
 FROM TAPE **=** { **'** _Name des physischen Sicherungsmediums_ **'**  |  **@** _physical_backup_device_name_var_ }  
  
###  <a name="TapeOptions"></a>Band spezifische Backup-und Restore-Optionen (Transact-SQL)  
 Zur Vereinfachung der Bandverwaltung bietet die BACKUP-Anweisung die folgenden bandspezifischen Optionen:  
  
-   { NOUNLOAD | **UNLOAD** }  
  
     Sie können steuern, ob ein Sicherungsband nach einem Sicherungs- oder Wiederherstellungsvorgang automatisch aus dem Bandlaufwerk ausgeworfen werden soll. UNLOAD/NOUNLOAD ist eine Sitzungseinstellung, die für die Dauer der Sitzung oder bis zur Angabe der alternativen Einstellung persistent gespeichert wird.  
  
-   { **REWIND** | NOREWIND }  
  
     Sie können steuern, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nach dem Sicherungs- oder Wiederherstellungsvorgang das Band offen hält oder das Band, wenn es voll ist, freigibt und zurückspult. Standardmäßig wird das Band zurückgespult (REWIND).  
  
> [!NOTE]  
>  Weitere Informationen zur Syntax und den Argumenten von BACKUP finden Sie unter [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql). Weitere Informationen zur Syntax und den Argumenten von RESTORE finden Sie unter [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) und [RESTORE-Argumente &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
###  <a name="OpenTapes"></a>Verwalten offener Bänder  
 Führen Sie eine Abfrage auf die dynamische Verwaltungssicht [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) aus, um eine Liste der offenen Bandmedien und den Status von Einbindungsanforderungen anzuzeigen. In dieser Sicht werden alle offenen Bänder angezeigt. Dies umfasst auch die gerade verwendeten Bänder, die sich bis zum nächsten BACKUP- oder RESTORE-Vorgang vorübergehend im Leerlauf befinden.  
  
 Wenn ein Band versehentlich offengeblieben ist, kann es am schnellsten mithilfe des folgenden Befehls freigegeben werden: RESTORE REWINDONLY FROM TAPE **=** _backup_device_name_. Weitere Informationen finden Sie unter [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql).  
  
## <a name="using-the-azure-blob-storage-service"></a>Verwenden des Azure BLOB Storage Dienstanbieter  
 SQL Server Sicherungen können in den Azure BLOB Storage-Dienst geschrieben werden.  Weitere Informationen zur Verwendung des Azure-BLOB-Speicher Dienstanbieter für Ihre Sicherungen finden Sie unter [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
##  <a name="LogicalBackupDevice"></a>Verwenden eines logischen Sicherungs Mediums  
 Ein *logisches Sicherungsmedium* ist ein optionaler, benutzerdefinierter Name, der auf ein bestimmtes, physisches Sicherungsmedium (Datenträgerdatei oder Bandlaufwerk) verweist. Ein logisches Sicherungsmedium gibt Ihnen beim Verweisen auf das entsprechende physische Sicherungsmedium die Möglichkeit zur Dereferenzierung.  
  
 Zum Definieren eines logischen Sicherungsmediums muss einem physischen Medium ein logischer Name zugeordnet werden. Beispielsweise kann ein logisches Medium (AdventureWorksBackups) so definiert werden, dass es auf die Datei „Z:\SQLServerBackups\AdventureWorks2012.bak“ oder das Bandlaufwerk „ \\\\.\tape0“ verweist. In Sicherungs- und Wiederherstellungsbefehlen kann dann AdventureWorksBackups anstelle von DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' or TAPE = '\\\\.\tape0' als Sicherungsmedium angegeben werden.  
  
 Der Name des logischen Mediums muss innerhalb der logischen Sicherungsmedien auf der Serverinstanz eindeutig sein. Sie können sich die vorhandenen logischen Mediennamen anzeigen lassen, indem Sie eine Abfrage für die [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) -Katalogsicht ausführen. In dieser Sicht wird der Name des logischen Sicherungsmediums angezeigt, und es wird der Typ und der physische Dateiname oder der Pfad des entsprechenden physischen Sicherungsmediums angegeben.  
  
 Nachdem ein logisches Sicherungsmedium definiert wurde, können Sie in einem BACKUP- oder RESTORE-Befehl das logische Sicherungsmedium angeben, statt den physischen Namen des Sicherungsmediums zu verwenden. Beispielsweise wird die `AdventureWorks2012` -Datenbank mit der folgenden Anweisung auf dem logischen Sicherungsmedium `AdventureWorksBackups` gesichert.  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO AdventureWorksBackups;  
GO  
```  
  
> [!NOTE]  
>  In jeder BACKUP- oder RESTORE-Anweisung kann wahlweise der logische Name des Sicherungsmediums oder der Name des entsprechenden physischen Sicherungsmediums angegeben werden.  
  
 Die Verwendung eines logischen Sicherungsmediums ist einfacher, da kein langer Pfad angegeben werden muss. Die Verwendung eines logischen Sicherungsmediums kann hilfreich sein, wenn Sie vorhaben, eine Reihe von Sicherungen auf denselben Pfad oder auf dasselbe Bandmedium zu schreiben. Logische Sicherungsmedien sind besonders nützlich zum Identifizieren von Bandsicherungsmedien.  
  
 Es kann ein Sicherungsskript geschrieben werden, um ein bestimmtes logisches Sicherungsmedium zu verwenden. Damit können Sie zu einem neuen physischen Sicherungsmedium wechseln, ohne dass ein Update des Skripts erforderlich ist. Für diesen Wechsel sind die folgenden Schritte erforderlich:  
  
1.  Löschen des ursprünglichen logischen Sicherungsmediums.  
  
2.  Definieren eines neuen logischen Sicherungsmediums, für das der Name des ursprünglichen logischen Sicherungsmediums verwendet wird, für das jedoch eine Zuordnung zu einem anderen physischen Sicherungsmedium erfolgt. Logische Sicherungsmedien sind besonders nützlich zum Identifizieren von Bandsicherungsmedien.  
  
##  <a name="MirroredMediaSets"></a>Gespiegelte Sicherungsmedien Sätze  
 Die Spiegelung von Sicherungsmediensätzen mindert die Auswirkungen von Funktionsstörungen bei Sicherungsmedien. Diese Funktionsstörungen sind besonders schwerwiegend, da Sicherungen im Hinblick auf den Verlust von Daten die letzte Schutzmaßnahme darstellen. Mit zunehmendem Umfang einer Datenbank nimmt auch die Wahrscheinlichkeit für einen Fehler bei einem Sicherungsgerät oder -medium zu, in dessen Folge eine Sicherung schließlich nicht mehr wiederhergestellt werden kann. Aufgrund der mit der Spiegelung von Sicherungsmedien bereitgestellten Redundanz für das physische Sicherungsmedium erhöht sich die Zuverlässigkeit von Sicherungen. Weitere Informationen finden Sie unter [Gespiegelte Sicherungsmediensätze &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).  
  
> [!NOTE]  
>  Gespiegelte Sicherungsmediensätze werden nur in [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] und höheren Versionen unterstützt.  
  
##  <a name="Archiving"></a>Archivieren von SQL Server Sicherungen  
 Datenträgersicherungen sollten mithilfe eines Hilfsprogramms für die Dateisystemsicherung archiviert und die Archive außerhalb des Standorts aufbewahrt werden. Das Verwenden eines Datenträgers hat den Vorteil, dass Sie die archivierten Sicherungen über das Netzwerk auf einen Datenträger außerhalb des Standorts schreiben können. Der Azure-BLOB-Speicherdienst kann als externe Archivierungs Option verwendet werden.  Sie können entweder die Datenträger Sicherungen hochladen oder die Sicherungen direkt in den Azure BLOB Storage-Dienst schreiben.  
  
 Eine weitere verbreitete Archivierungsmethode besteht darin, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen auf einen lokalen Sicherungsdatenträger zu schreiben, auf Band zu archivieren und die Bänder außerhalb des Standorts aufzubewahren.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So geben Sie ein Datenträgermedium an (SQL Server Management Studio)**  
  
-   [Angeben eines Datenträgers oder ein Bands als Sicherungsziel &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 **So geben Sie ein Bandmedium an (SQL Server Management Studio)**  
  
-   [Angeben eines Datenträgers oder ein Bands als Sicherungsziel &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 **So definieren Sie ein logisches Sicherungsmedium**  
  
-   [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
-   [Definieren eines logischen Sicherungsmediums für eine Datenträgerdatei &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)  
  
 **So verwenden Sie ein logisches Sicherungsmedium**  
  
-   [Angeben eines Datenträgers oder ein Bands als Sicherungsziel &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [Wiederherstellung einer Sicherung von einem Medium &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)  
  
-   [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
 **So zeigen Sie Informationen zu Sicherungsmedien an**  
  
-   [Sicherungsverlauf und Headerinformationen &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md)  
  
-   [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [Anzeigen der Inhalte eines Sicherungsbands oder einer -datei &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
 **So löschen Sie ein logisches Sicherungsmedium**  
  
-   [sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)  
  
-   [Löschen eines Sicherungsmediums &#40;SQL Server&#41;](delete-a-backup-device-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server, Sicherungsmedium-Objekt](../performance-monitor/sql-server-backup-device-object.md)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Wartungspläne](../maintenance-plans/maintenance-plans.md)   
 [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql)   
 [sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql)   
 [Gespiegelte Sicherungsmediensätze &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)  
  
  
