---
title: MSSQLSERVER_17204 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/25/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a094a2baf20ccdf29514a82f4ff749c6d9e18be3
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87236076"
---
# <a name="mssqlserver_17204"></a>MSSQLSERVER_17204
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |
| :-------- | :---- |
|Produktname|SQL Server|  
|Ereignis-ID|17204|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBLKIO_DEVOPENFAILED|  
|Meldungstext|%ls: Die Datei %ls für die Dateinummer %d konnte nicht geöffnet werden.  Betriebssystemfehler: %ls.|  
  
## <a name="explanation"></a>Erklärung  
SQL Server konnte die angegebene Datei aufgrund des angegebenen Betriebssystemfehlers nicht öffnen.  

Möglicherweise wird im Windows-Anwendungsereignis- oder im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll Fehler 17204 verzeichnet, wenn SQL Server eine Datenbank und/oder Dateien des Transaktionsprotokolls nicht öffnen kann. Hier sehen Sie ein weiteres Beispiel dafür, wie dieser Fehler aussehen kann:

``` 
Error: 17204, Severity: 16, State: 1.
FCB::Open failed: Could not open file c:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\data\MyDB_Prm.mdf for file number 1.  OS error: 5(Access is denied.).
```

Möglicherweise begegnen Ihnen diese Fehler während des Startvorgangs der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz oder während anderer Datenbankvorgänge, die versuchen, die Datenbank zu starten (z. B. ALTER DATABASE). In manchen Szenarien können sowohl 17204- als auch 17207-Fehler auftreten, und bei anderen Gelegenheiten sehen Sie nur einen von beiden.

Wenn diese Fehler bei einer Benutzerdatenbank auftreten, verbleibt die Datenbank im Status RECOVERY_PENDING, und Anwendungen können nicht auf die Datenbank zugreifen. Wenn diese Fehler bei einer Systemdatenbank auftreten, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz nicht gestartet, und Sie können keine Verbindung mit dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen. Ein Fehler in einer Systemdatenbank könnte auch dazu führen, dass eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusterressource in den Offlinemodus versetzt wird.

## <a name="cause"></a>Ursache
Bevor eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank verwendet werden kann, muss die Datenbank gestartet werden. Der Datenbank-Startvorgang umfasst die folgenden Schritte: 
1. Initialisieren verschiedener Datenstrukturen, die die Datenbank und die Datenbankdateien darstellen
1. Öffnen aller Dateien, die zur Datenbank gehören
1. Ausführen der Wiederherstellung für die Datenbank 

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet die Windows-API-Funktion [CreateFile](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-createfilea), um die Dateien zu öffnen, die zu einer Datenbank gehören.
 
Die Nachrichten 17204 (und 17207) weisen darauf hin, dass ein Fehler auftrat, während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versuchte, die Datenbankdateien während des Startvorgangs zu öffnen.
 
Diese Fehlermeldungen enthalten die folgenden Informationen:
1. Den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktion, die versucht, die Datei zu öffnen. Der Funktionsname, den Sie normalerweise in diesen Fehlermeldungen finden, ist einer der folgenden:
   - FCB::Open: Bei der Datei ist ein Fehler aufgetreten, als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sie zu öffnen versuchte
   - FileMgr::StartPrimaryDataFiles: Eine primäre Datendatei oder eine Datei, die der primären Dateigruppe angehört
   - FileMgr::StartSecondaryDataFiles: Eine Datei, die zu einer sekundären Dateigruppe gehört
   - FileMgr::StartLogFiles: Eine Transaktionsprotokolldatei
   - STREAMFCB::Startup: SQL FileStream-Container
   - FCB::RemoveAlternateStreams
  
      
1. Die Statusinformationen unterscheiden mehrere Orte innerhalb einer Funktion, die diese Fehlermeldung generieren kann
1. Der vollständige physische Pfad der Datei
1. Die Datei-ID der Datei
1. Der Betriebssystem-Fehlercode und die Fehlerbeschreibung. In manchen Fällen sehen Sie nur den Fehlercode.
 
Die Betriebssystem-Fehlerinformationen die in diesen Fehlermeldungen angegeben werden, bilden die Grundursache, die zu Fehler 17204 geführt hat. Häufige Gründe für diese Fehlermeldungen sind ein Berechtigungsproblem oder ein nicht ordnungsgemäßer Dateipfad.


## <a name="user-action"></a>Benutzeraktion  
1. Voraussetzung zum Beheben von Fehler 17204 sind das Verständnis des zugehörigen Betriebssystem-Fehlercodes und die Diagnose des Fehlers. Nach dem Beheben der Betriebssystem-Fehlerbedingung können Sie versuchen, die Datenbank neu zu starten (beispielsweise mithilfe von ALTER DATABASE SET ONLINE) oder die betroffene Datenbank durch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz online schalten zu lassen. In einigen Fällen gelingt es Ihnen möglicherweise nicht, den Betriebssystemfehler zu beheben. Dann müssen Sie bestimmte Korrekturmaßnahmen ergreifen. Wir behandeln diese Aktionen in diesem Abschnitt.
1. Wenn die 17204-Fehlermeldung nur einen Fehlercode und keine Fehlerbeschreibung enthält, können Sie versuchen, den Fehlercode mithilfe des folgenden Befehls an einer Betriebssystemshell aufzulösen: net helpmsg <error code> . Wenn Sie einen 8stelligen Statuscode als Fehlercode erhalten, können Sie auf Informationsquellen wie [How do I convert an HRESULT to a Win32 error code?](https://devblogs.microsoft.com/oldnewthing/20061103-07/?p=29133) (Gewusst wie: Konvertieren eines HRESULT-Werts in einen Win32-Fehlercode) zurückgreifen, um diese Statuscodes in Betriebssystemfehler zu decodieren.
1. Wenn Sie den `Access is Denied`-Betriebssystemfehler „5“ empfangen, ziehen Sie diese Methoden in Erwägung:
   -  Überprüfen Sie die für die Datei festgelegten Berechtigungen, indem Sie die Eigenschaften der Datei im Windows-Explorer untersuchen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet Windows-Gruppen, um Zugriffssteuerung für die verschiedenen Dateiressourcen bereitzustellen. Vergewissern Sie sich, dass die entsprechende Gruppe [mit Namen wie SQLServerMSSQLUser$ComputerName$MSSQLSERVER oder SQLServerMSSQLUser$ComputerName$InstanceName] über die erforderlichen Berechtigungen für die Datenbankdatei verfügt, die in der Fehlermeldung genannt wird. Weitere Informationen finden Sie unter [Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff](/previous-versions/sql/2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access?view=sql-server-2014). Achten Sie darauf, dass die Windows-Gruppe das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienststartkonto oder die Dienst-SID tatsächlich enthält.
   -  Überprüfen Sie das Benutzerkonto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst aktuell ausgeführt wird. Sie können diese Informationen mithilfe des Windows Task-Managers abrufen. Suchen Sie nach dem Wert für „Benutzername“ der „sqlservr.exe“-Programmdatei. Wenn Sie vor Kurzem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto geändert haben, berücksichtigen Sie außerdem, dass bei der unterstützten Durchführung dieses Vorgangs das SQL Server-Konfigurations-Manager-Hilfsprogramm verwendet wird. Weitere Informationen dazu finden Sie unter [SQL Server-Konfigurations-Manager](../sql-server-configuration-manager.md). 
   -  Abhängig vom Typ des Vorgangs – Öffnen von Datenbanken während des Serverstarts, Anfügen einer Datenbank, Datenbankwiederherstellung usw. – kann das Konto, das für Identitätswechsel und den Zugriff auf die Datenbankdatei verwendet wird, abweichen. Arbeiten Sie das Thema [Sichern von Daten- und Protokolldateien](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)?redirectedfrom=MSDN) durch, um zu verstehen, welcher Vorgang welche Berechtigungen für welche Konten festlegt. Verwenden Sie ein Tool wie den [Prozessmonitor](https://docs.microsoft.com/sysinternals/downloads/procmon) von Windows SysInternals, um zu verstehen, ob der Dateizugriff unter dem Sicherheitskontext des Dienststartkontos der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz [oder Dienst-SID] oder einem Konto mit Identitätswechsel erfolgt.

      Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Anmeldeinformationen des Benutzers, mit dem der ALTER DATABASE- oder CREATE DATABASE-Vorgang ausgeführt wird, durch Identitätswechsel darstellt, können Sie im Prozessmonitor-Tool die folgenden Informationen finden (Beispiel):
        ```Date & Time:      3/27/2010 8:26:08 PM
        Event Class:        File System
        Operation:          CreateFile
        Result:                ACCESS DENIED
        Path:                  C:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\DATA\attach_test.mdf
        TID:                   4288
        Duration:             0.0000366
        Desired Access:Generic Read/Write
        Disposition:        Open
        Options:            Synchronous IO Non-Alert, Non-Directory File, Open No Recall
        Attributes:          N
        ShareMode:       Read
        AllocationSize:   n/a
        Impersonating: DomainName\UserName```
  
1. If you are getting `The system cannot find the file specified` OS error = 3:
   - Review the complete path from the error message
   - Ensure the disk drive and the folder path is visible and accessible from Windows Explorer
   - Review the Windows Event log to find out if any problems exist with this disk drive
   - If the path is incorrect and if this database already exists in the system, you can change the database file paths using the methods explained in the topic [Move Database Files](../databases/move-database-files.md). You may have to use this procedure, especially for system database files that encounter 17204 or 17207 and you are working through a disaster recovery scenario where the specified disk drives are unavailable. This topic also explains how you can identify the current location of the various system databases [master, model, tempdb, msdb and mssqlsystemresource].
   - If you see this error because the database files are missing, you have to restore the database from a valid backup.
     - If the database file associated with the error belongs to a secondary filegroup, then you can optionally mark that filegroup offline, bring the database online and then perform a restore of that filegroup alone. For more information, refer to the OFFLINE section of the topic [ALTER DATABASE File and Filegroup Options (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).
     - If the file that produced the error is a transaction log file, review the information under the sections "FOR ATTACH" and "FOR ATTACH_REBUILD_LOG" of the topic [CREATE DATABASE (Transact-SQL)](../../t-sql/statements/create-database-transact-sql.md) to understand how you can recreate the missing transaction log files.
   - Ensure that any disk or network location [like iSCSI drive] is available before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attempts to access the database files on these locations. If needed create the required dependencies in Cluster Administrator or Service Control Manager.
1. If you're getting the `The process cannot access the file because it is being used by another process` operating system error = 32:
   - Use a tool like [Process Explorer](https://docs.microsoft.com/sysinternals/downloads/process-explorer) or [Handle](https://docs.microsoft.com/sysinternals/downloads/handle) from Windows Sysinternals to find out if another process or service has acquired exclusive lock on this database file
   - Stop that process from accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database files. Common examples include anti-virus programs (see guidance for file exclusions in the following [KB article](https://support.microsoft.com/help/309422/choosing-antivirus-software-for-computers-that-run-sql-server) )
   - In a cluster environment, make sure that the sqlservr.exe process from the previous owning node has actually released the handles to the database files. Normally, this doesn't occur, but misconfigurations of the cluster or I/O paths can lead to such issues.
  
