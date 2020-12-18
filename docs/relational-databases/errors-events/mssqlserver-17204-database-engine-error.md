---
description: MSSQLSERVER_17204
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
ms.openlocfilehash: 996650e8552f435240663d61bf3734f875e2210a
ms.sourcegitcommit: 28fecbf61ae7b53405ca378e2f5f90badb1a296a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96595180"
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

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet die Windows-API-Funktion [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea), um die Dateien zu öffnen, die zu einer Datenbank gehören.
 
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
   -  Überprüfen Sie die für die Datei festgelegten Berechtigungen, indem Sie die Eigenschaften der Datei im Windows-Explorer untersuchen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet Windows-Gruppen, um Zugriffssteuerung für die verschiedenen Dateiressourcen bereitzustellen. Vergewissern Sie sich, dass die entsprechende Gruppe [mit Namen wie SQLServerMSSQLUser$ComputerName$MSSQLSERVER oder SQLServerMSSQLUser$ComputerName$InstanceName] über die erforderlichen Berechtigungen für die Datenbankdatei verfügt, die in der Fehlermeldung genannt wird. Weitere Informationen finden Sie unter [Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff](/previous-versions/sql/2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access). Achten Sie darauf, dass die Windows-Gruppe das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienststartkonto oder die Dienst-SID tatsächlich enthält.
   -  Überprüfen Sie das Benutzerkonto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst aktuell ausgeführt wird. Sie können diese Informationen mithilfe des Windows Task-Managers abrufen. Suchen Sie nach dem Wert für „Benutzername“ der „sqlservr.exe“-Programmdatei. Wenn Sie vor Kurzem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto geändert haben, berücksichtigen Sie außerdem, dass bei der unterstützten Durchführung dieses Vorgangs das SQL Server-Konfigurations-Manager-Hilfsprogramm verwendet wird. Weitere Informationen dazu finden Sie unter [SQL Server-Konfigurations-Manager](../sql-server-configuration-manager.md). 
   -  Abhängig vom Typ des Vorgangs – Öffnen von Datenbanken während des Serverstarts, Anfügen einer Datenbank, Datenbankwiederherstellung usw. – kann das Konto, das für Identitätswechsel und den Zugriff auf die Datenbankdatei verwendet wird, abweichen. Arbeiten Sie das Thema [Sichern von Daten- und Protokolldateien](/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)) durch, um zu verstehen, welcher Vorgang welche Berechtigungen für welche Konten festlegt. Verwenden Sie ein Tool wie den [Prozessmonitor](/sysinternals/downloads/procmon) von Windows SysInternals, um zu verstehen, ob der Dateizugriff unter dem Sicherheitskontext des Dienststartkontos der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz [oder Dienst-SID] oder einem Konto mit Identitätswechsel erfolgt.

      Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Anmeldeinformationen des Benutzers, mit dem der ALTER DATABASE- oder CREATE DATABASE-Vorgang ausgeführt wird, durch Identitätswechsel darstellt, können Sie im Prozessmonitor-Tool die folgenden Informationen finden (Beispiel):
        
        ```output
        Date & Time:      3/27/2010 8:26:08 PM
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
        Impersonating: DomainName\UserName
        ```
  
1. Wenn Sie den Betriebssystemfehler 3 `The system cannot find the file specified` erhalten:
   - Überprüfen Sie den gesamten Pfad aus der Fehlermeldung.
   - Stellen Sie sicher, dass das Laufwerk und der Ordnerpfad im Windows-Explorer sichtbar und zugänglich sind.
   - Überprüfen Sie im Windows-Ereignisprotokoll, ob Probleme mit diesem Laufwerk vorliegen.
   - Wenn der Pfad falsch und diese Datenbank bereits im System vorhanden ist, können Sie den Pfad der Datenbankdatei mithilfe der Anleitungen im Thema [Verschieben von Datenbankdateien](../databases/move-database-files.md) ändern. Möglicherweise müssen Sie dieses Verfahren anwenden, wenn bei Systemdatenbankdateien ein Fehler des Typs 17204 oder 17207 auftritt und Sie ein Notfallwiederherstellungsszenario durcharbeiten, in dem die angegebenen Laufwerke nicht verfügbar sind. In diesem Thema wird auch erläutert, wie Sie den aktuellen Speicherort der verschiedenen Systemdatenbanken (master, model, tempdb, msdb und mssqlsystemresource) herausfinden können.
   - Wenn dieser Fehler angezeigt wird, weil die Datenbankdateien fehlen, müssen Sie die Datenbank aus einer gültigen Sicherung wiederherstellen.
     - Wenn die Datenbankdatei, auf die sich die Fehlermeldung bezieht, zu einer sekundären Dateigruppe gehört, können Sie diese Dateigruppe optional als offline markieren, die Datenbank online schalten und dann nur diese Dateigruppe wiederherstellen. Weitere Informationen finden Sie im OFFLINE-Abschnitt des Themas [ALTER DATABASE-Optionen für Dateien und Dateigruppen (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).
     - Wenn die Datei, die den Fehler erzeugt hat, eine Transaktionsprotokolldatei ist, sollten Sie die Abschnitte zu „FOR ATTACH“ und „FOR ATTACH_REBUILD_LOG“ im Thema [Create Database](../../t-sql/statements/create-database-transact-sql.md) lesen, um zu verstehen, wie Sie die fehlenden Transaktionsprotokolldateien neu erstellen können.
   - Stellen Sie sicher, dass ein beliebiger Datenträger oder eine beliebige Netzwerkadresse (z. B. ein iSCSI-Laufwerk) verfügbar ist, bevor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht, auf die Datenbankdateien an diesen Speicherorten zuzugreifen. Bei Bedarf können Sie die erforderlichen Abhängigkeiten in der Clusterverwaltung oder im Dienststeuerungs-Manager erstellen.
1. Wenn Sie den Betriebssystemfehler 32 `The process cannot access the file because it is being used by another process` erhalten:
   - Mit Windows Sysinternals-Tools wie [Process Explorer](/sysinternals/downloads/process-explorer) oder [Handle](/sysinternals/downloads/handle) können Sie herausfinden, ob ein anderer Prozess oder Dienst eine exklusive Sperre für diese Datenbankdatei erhalten hat.
   - Verhindern Sie, dass dieser Prozess auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbankdateien zugreift. Häufige Beispiele hierfür sind Virenschutzprogramme (Informationen zu Dateiausnahmen finden Sie in [diesem KB-Artikel](https://support.microsoft.com/help/309422/choosing-antivirus-software-for-computers-that-run-sql-server)).
   - Stellen Sie in einer Clusterumgebung sicher, dass der Prozess „sqlservr.exe“ aus dem vorherigen besitzenden Knoten tatsächlich die Handles für die Datenbankdateien freigegeben hat. Solche Probleme treten in der Regel nicht auf, aber Fehlkonfigurationen des Clusters oder der E/A-Pfade können zu solchen Problemen führen.
