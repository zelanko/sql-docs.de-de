---
title: MSSQLSERVER_5228 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5120 (Database Engine error)
ms.assetid: ''
author: PijoCoder
ms.author: mathoma
ms.openlocfilehash: ff8fb262b643390f2914a4a5e6c42dcc887206f8
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "81728617"
---
# <a name="mssqlserver_5120"></a>MSSQLSERVER_5120
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|5120|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DSK_FCB_FAILURE|  
|Meldungstext|Tabellenfehler: Die physische Datei '%.*ls' kann nicht geöffnet werden. Betriebssystemfehler %d: '%ls'.|  
  
## <a name="explanation"></a>Erklärung  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte eine Datenbankdatei nicht öffnen.  Der in der Meldung angegebene Betriebssystemfehler verweist auf die zugrunde liegenden spezifischeren Ursachen des Fehlers. Dieser Fehler tritt häufig in Kombination mit anderen Fehlern wie [17204](mssqlserver-17204-database-engine-error.md) oder [17207](mssqlserver-17207-database-engine-error.md) auf.
  
## <a name="user-action"></a>Benutzeraktion  
  
  Diagnostizieren und korrigieren Sie den Betriebssystemfehler, und wiederholen Sie dann den Vorgang. Es gibt mehrere Zustände, die Microsoft dabei helfen können, den Bereich im Produkt einzugrenzen, in dem der Fehler auftritt. 
  
### <a name="access-is-denied"></a>Zugriff verweigert 
Wenn Sie den ```Access is Denied```-Betriebssystemfehler „5“ empfangen, ziehen Sie diese Methoden in Erwägung:
   -  Überprüfen Sie die für die Datei festgelegten Berechtigungen, indem Sie die Eigenschaften der Datei im Windows-Explorer untersuchen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet Windows-Gruppen, um Zugriffssteuerung für die verschiedenen Dateiressourcen bereitzustellen. Vergewissern Sie sich, dass die entsprechende Gruppe [mit Namen wie SQLServerMSSQLUser$ComputerName$MSSQLSERVER oder SQLServerMSSQLUser$ComputerName$InstanceName] über die erforderlichen Berechtigungen für die Datenbankdatei verfügt, die in der Fehlermeldung genannt wird. Weitere Details finden Sie unter [Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff](../../2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access.md). Achten Sie darauf, dass die Windows-Gruppe das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienststartkonto oder die Dienst-SID tatsächlich enthält.
   -  Überprüfen Sie das Benutzerkonto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst aktuell ausgeführt wird. Sie können diese Informationen mithilfe des Windows Task-Managers abrufen. Suchen Sie nach dem Wert für „Benutzername“ der „sqlservr.exe“-Programmdatei. Wenn Sie vor Kurzem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto geändert haben, berücksichtigen Sie außerdem, dass bei der unterstützten Durchführung dieses Vorgangs das [SQL Server-Konfigurations-Manager](../sql-server-configuration-manager.md)-Hilfsprogramm verwendet wird. 
   -  Abhängig vom Typ des Vorgangs – Öffnen von Datenbanken während des Serverstarts, Anfügen einer Datenbank, Datenbankwiederherstellung usw. – kann das Konto, das für Identitätswechsel und den Zugriff auf die Datenbankdatei verwendet wird, abweichen. Arbeiten Sie das Thema [Sichern von Daten- und Protokolldateien](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)?redirectedfrom=MSDN) durch, um zu verstehen, welcher Vorgang welche Berechtigungen für welche Konten festlegt. Verwenden Sie ein Tool wie den [Prozessmonitor](https://docs.microsoft.com/sysinternals/downloads/procmon) von Windows SysInternals, um zu verstehen, ob der Dateizugriff unter dem Sicherheitkontext des Dienststartkontos der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz [oder Dienst-SID] oder einem Konto mit Identitätswechsel erfolgt.

      Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Benutzeranmeldeinformationen der Anmeldung, mit der der ALTER DATABASE- oder CREATE DATABASE-Vorgang ausgeführt wird, durch Identitätswechsel darstellt, können Sie im Prozessmonitor-Tool die folgenden Informationen finden (Beispiel):
        ```Date & Time:      3/27/2010 8:26:08 PM
        Event Class:        File System
        Operation:          CreateFile
        Result:                ACCESS DENIED
        Path:                  C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\DATA\attach_test.mdf
        TID:                   4288
        Duration:             0.0000366
        Desired Access:Generic Read/Write
        Disposition:        Open
        Options:            Synchronous IO Non-Alert, Non-Directory File, Open No Recall
        Attributes:          N
        ShareMode:       Read
        AllocationSize:   n/a
        Impersonating: DomainName\UserName```
  
  
### Attaching Files that Reside on a Network-attached storage  
If you cannot re-attach a database that resides on network-attached storage, a message like this may be logged in the Application log:

```Msg 5120, Level 16, State 101, Line 1 Unable to open the physical file "\\servername\sharename\filename.mdf". Operating system error 5: (Access is denied.).```

This problem occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resets the file permissions when the database is detached. When you try to reattach the database, a failure occurs because of limited share permissions.

To resolve, follow these steps:
1. Use the -T startup option to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use this startup option to turn on trace flag 1802 in [SQL Server Configuration Manager](../sql-server-configuration-manager.md) (see [Trace Flags](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md) for information on 1802). For more information about how to change the startup parameters, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)

2. Use the following command to detach the database.
```tsql
 exec sp_detach_db DatabaseName
 go 
```

3. Verwenden Sie den folgenden Befehl, um die Datenbank erneut anzufügen.
```tsql
exec sp_attach_db DatabaseName, '\\Network-attached storage_Path\DatabaseMDFFile.mdf', '\\Network-attached storage_Path\DatabaseLDFFile.ldf'
go
```
 
