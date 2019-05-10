---
title: Verwalten von SQLServer unter Linux mit PowerShell Core | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Übersicht über die Verwendung von PowerShell Core mit SQL Server unter Linux
ms.date: 04/22/2019
ms.reviewer: jroth
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
manager: craigg
ms.openlocfilehash: 0fed98dd418113f92557c9993a11c21b610f07c4
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135268"
---
# <a name="manage-sql-server-on-linux-with-powershell-core"></a>Verwalten von SQLServer unter Linux mit PowerShell Core

In diesem Artikel werden [SQL Server PowerShell](../powershell/sql-server-powershell.md) und führt Sie durch ein paar Beispiele zur Verwendung mit dem PowerShell Core (PS-Core) in MacOS und Linux. PowerShell Core ist jetzt Open Source-Projekt [GitHub](https://github.com/powershell/powershell).

## <a name="cross-platform-editor-options"></a>Cross-Platform-Editor-Optionen

Funktioniert PowerShell Core, die unten beschriebenen Schritte in einem regulären Terminal aus, oder können Sie sie über ein Terminal in VS Code oder Azure Data Studio ausführen.  Sowohl Visual Studio Code und Azure Data Studio stehen unter MacOS und Linux zur Verfügung.  Weitere Informationen zu Azure Data Studio, finden Sie unter [in dieser schnellstartanleitung](https://docs.microsoft.com/sql/azure-data-studio/quickstart-sql-server).  Sie sollten auch erwägen, stattdessen die [PowerShell-Erweiterung](https://docs.microsoft.com/sql/azure-data-studio/powershell-extension) dafür.

## <a name="installing-powershell-core"></a>Installieren von PowerShell Core

Weitere Informationen zum Installieren von PowerShell Core auf verschiedenen Plattformen mit unterstützten und experimentelle finden Sie unter den folgenden Artikeln:

- [Installieren von PowerShell Core unter Windows](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6)
- [Installieren von PowerShell Core unter Linux](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [Installieren von PowerShell Core unter macOS](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)
- [Installieren von PowerShell Core für ARM](https://docs.microsoft.com/powershell/scripting/install/powershell-core-on-arm?view=powershell-6)

## <a name="install-the-sqlserver-module"></a>Installieren Sie das SqlServer-Modul

Die `SqlServer` Modul werden in der [PowerShell-Katalog](https://www.powershellgallery.com/packages/SqlServer/). Bei der Arbeit mit SQL Server sollten Sie immer die neueste Version des SqlServer PowerShell-Moduls verwenden.

Um das SqlServer-Modul zu installieren, öffnen Sie eine PowerShell-Kern-Sitzung, und führen Sie den folgenden Code:

```powerhsell
Install-Module -Name SqlServer
```

Weitere Informationen zum Installieren des SqlServer-Moduls aus dem PowerShell-Katalog finden Sie in diesem [Seite](../powershell/download-sql-server-ps-module.md).

## <a name="using-the-sqlserver-module"></a>Verwenden das SqlServer-Modul

Beginnen wir mit PowerShell Core starten.  Unter MacOS oder Linux, öffnen Sie möchten eine *Terminalsitzung* auf den Computer, und geben **Pwsh** um eine neue PowerShell Core-Sitzung zu starten.  Verwenden Sie für Windows, <kbd>gewinnen</kbd>+<kbd>R</kbd>, und geben `pwsh` um eine neue PowerShell Core-Sitzung zu starten.

```
pwsh
```

SQL Server bietet ein PowerShell-Modul, das mit dem Namen **SqlServer**. Sie können die **SqlServer** Module zum Importieren von SQL Server-Komponenten (SQL Server-Anbieter und Cmdlets) in einer PowerShell-Umgebung oder einem Skript.

Kopieren Sie den folgenden Befehl an der PowerShell-Eingabeaufforderung zum Importieren der **SqlServer** Modul in Ihrer aktuellen PowerShell-Sitzung:

```powershell
Import-Module SqlServer
```

Geben Sie den folgenden Befehl an der PowerShell-Eingabeaufforderung zu überprüfen, ob die **SqlServer** Modul ordnungsgemäß importiert wurde:

```powershell
Get-Module -Name SqlServer
```

PowerShell sollte Informationen ähnlich wie die folgende Ausgabe angezeigt werden:

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     21.1.18102 SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Verbinden mit SQL Server, und erhalten Sie Informationen zum server

Die folgenden Schritte verwenden PowerShell Core eine Verbindung mit Ihrer SQL Server-Instanz unter Linux, und eine Reihe von Servereigenschaften anzuzeigen.

Kopieren Sie die folgenden Befehle an der PowerShell-Eingabeaufforderung. Wenn Sie diese Befehle ausführen, wird PowerShell aus:
- Ein Dialogfeld, das Sie, für den Hostnamen oder IP-Adresse der Instanz auffordert angezeigt
- Anzeigen der *PowerShell anmelden* Dialogfeld, in dem Sie die Anmeldeinformationen dazu aufgefordert werden. Sie können Ihrer *SQL-Benutzernamen* und *SQL-Kennwort* zur Verbindung mit Ihrer SQL Server-Instanz unter Linux
- Verwenden der **Get-SqlInstance** -Cmdlet zum Herstellen einer Verbindung mit der **Server** und einige Eigenschaften anzeigen

Optional können Sie einfach ersetzen die `$serverInstance` Variable mit dem die IP-Adresse oder den Hostnamen Ihrer SQL Server-Instanz.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Connect to the Server and return a few properties
Get-SqlInstance -ServerInstance $serverInstance -Credential $credential
# done
```

PowerShell sollte Informationen ähnlich wie die folgende Ausgabe angezeigt werden:

```
Instance Name                   Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------                   -------    ------------ -----------  ------------ ----------------
your_server_instance            14.0.3048  RTM          CU13         Linux        Ubuntu
```

> [!NOTE]
> Wenn nichts für diese Werte angezeigt wird, konnte die Verbindung mit der SQL Server-Zielinstanz in den meisten Fällen nicht. Stellen Sie sicher, dass Sie dieselben Verbindungsinformationen für die Verbindung von SQL Server Management Studio verwenden können. Überprüfen Sie anschließend die [Empfehlungen zur Verbindungsproblembehandlung](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="using-the-sql-server-powershell-provider"></a>Verwenden von SQL Server PowerShell-Anbieter

Eine weitere Option für die Verbindung mit Ihrer SQL Server-Instanz ist die Verwendung der [SQL Server PowerShell Provider](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider).  Mit dem Anbieter, können Sie SQL Server-Instanz, die ähnlich wie wenn Sie die Baumstruktur im Objekt-Explorer, sondern auf der Befehlszeile navigiert wurden navigieren.  Dieser Anbieter wird standardmäßig als ein PSDrive, das mit dem Namen angezeigt `SQLSERVER:\` die Sie verwenden können, zu verbinden, und navigieren SQL Server-Instanzen, die Ihr Domänenkonto Zugriff hat.  Finden Sie unter [Konfigurationsschritte](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps) für Informationen zum Einrichten von Active Directory-Authentifizierung für SQL Server unter Linux.

Sie können auch SQL-Authentifizierung mit SQL Server PowerShell-Anbieter verwenden. Verwenden Sie hierzu die `New-PSDrive` Cmdlet erstellen ein neues PSDrive, und geben Sie die richtigen Anmeldeinformationen eine Verbindung herstellen.

In diesem Beispiel sehen Sie ein Beispiel dafür, wie ein neues PSDrive, das mit SQL-Authentifizierung zu erstellen.

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.

New-PSDrive -Name SQLonDocker -PSProvider SqlServer -Root 'SQLSERVER:\SQL\localhost,10002\Default\' -Credential $credential
```

Sie können bestätigen, dass das Laufwerk, durch Ausführen erstellt wurde der `Get-PSDrive` Cmdlet.

```powershell
Get-PSDrive
```

Nachdem Sie Ihr neues PSDrive erstellt haben, können Sie beginnen, wo es.

```powershell
dir SQLonDocker:\Databases
```

Hier ist die Ausgabe könnte folgendermaßen aussehen.  Sie können feststellen, diese Ausgabe ist ähnlich wie SSMS auf den Knoten "Datenbanken" angezeigt wird.  Es zeigt die Benutzerdatenbanken, jedoch nicht in den Systemdatenbanken.

```powershell
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2016   Normal      209.63 MB    1.31 MB Simple       130 sa
AdventureWorksDW2012 Normal      167.00 MB   32.47 MB Simple       110 sa
AdventureWorksDW2014 Normal      188.00 MB   78.10 MB Simple       120 sa
AdventureWorksDW2016 Normal      172.00 MB   74.76 MB Simple       130 sa
AdventureWorksDW2017 Normal      208.00 MB   40.57 MB Simple       140 sa
```

Wenn Sie alle Datenbanken in Ihrer Instanz angezeigt müssen, eine Möglichkeit ist die Verwendung der `Get-SqlDatabase` Cmdlet.

## <a name="get-databases"></a>Abrufen von Datenbanken.

Eine wichtige Cmdlet wissen, ist die `Get-SqlDatabase`.  Für viele Vorgänge, bei denen eine Datenbank oder Objekte innerhalb einer Datenbank, die `Get-SqlDatabase` Cmdlet kann verwendet werden.  Wenn Sie Werte für beide angeben der `-ServerInstance` und `-Database` Parameter nur dieses eine Datenbank-Objekt abgerufen werden soll.  Aber wenn Sie nur angeben der `-ServerInstance` Parameter, eine vollständige Liste aller Datenbanken in dieser Instanz zurückgegeben.

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.

# Connect to the Instance and retrieve all databases
Get-SqlDatabase -ServerInstance ServerB -Credential $credential
```

Hier ist ein Beispiel der von der oben aufgeführten Get-SqlDatabase-Befehl zurückgegeben werden kann:

```powershell
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2016   Normal      209.63 MB    1.31 MB Simple       130 sa
AdventureWorksDW2012 Normal      167.00 MB   32.47 MB Simple       110 sa
AdventureWorksDW2014 Normal      188.00 MB   78.10 MB Simple       120 sa
AdventureWorksDW2016 Normal      172.00 MB   74.88 MB Simple       130 sa
AdventureWorksDW2017 Normal      208.00 MB   40.63 MB Simple       140 sa
master               Normal        6.00 MB  600.00 KB Simple       140 sa
model                Normal       16.00 MB    5.70 MB Full         140 sa
msdb                 Normal       15.50 MB    1.14 MB Simple       140 sa
tempdb               Normal       16.00 MB    5.49 MB Simple       140 sa

```

## <a name="examine-sql-server-error-logs"></a>SQL Server-Fehlerprotokollen

Die folgenden Schritte verwenden PowerShell Core, um Fehler zu untersuchen, die Protokolle, die auf Ihre SQL Server-Instanz unter Linux eine Verbindung her.

Kopieren Sie die folgenden Befehle an der PowerShell-Eingabeaufforderung. Sie können einige Minuten dauern. Diese Befehle führen die folgenden Schritte aus:
- Ein Dialogfeld, das Sie, für den Hostnamen oder IP-Adresse der Instanz auffordert angezeigt
- Anzeigen der *PowerShell anmelden* Dialogfeld, das Sie für die Anmeldeinformationen aufgefordert werden. Sie können Ihrer *SQL-Benutzernamen* und *SQL-Kennwort* zur Verbindung mit Ihrer SQL Server-Instanz unter Linux
- Verwenden der **Get-SqlErrorLog** Cmdlet, um eine Verbindung mit SQL Server-Instanz unter Linux herstellen und Abrufen von Fehler protokolliert, da **gestern**

Optional können Sie ersetzen die `$serverInstance` Variable mit dem die IP-Adresse oder den Hostnamen Ihrer SQL Server-Instanz.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday
# done
```

## <a name="explore-cmdlets-currently-available-in-ps-core"></a>Durchsuchen von Cmdlets, die derzeit in der PS-Core verfügbar
Während das SqlServer-Modul zurzeit 106 Cmdlets in Windows PowerShell verfügbar ist, sind nur 59 die 106 in PSCore verfügbar. Eine vollständige Liste der derzeit verfügbaren 59 Cmdlets ist unten enthalten.  Ausführliche Dokumentation aller Cmdlets im SqlServer-Modul finden Sie im SqlServer [Cmdlet-Referenz](https://docs.microsoft.com/powershell/module/sqlserver/).

Der folgende Befehl zeigt aller verfügbaren Cmdlets auf die Version von PowerShell Ihnen, die Sie verwenden.

```powershell
Get-Command -Module SqlServer -CommandType Cmdlet |
SORT -Property Noun |
SELECT Name
```

- ConvertFrom-EncodedSqlName
- ConvertTo-EncodedSqlName
- Get-SqlAgent
- Get-SqlAgentJob
- Get-SqlAgentJobHistory
- Get-SqlAgentJobSchedule
- Get-SqlAgentJobStep
- Get-SqlAgentSchedule
- Remove-SqlAvailabilityDatabase
- Resume-SqlAvailabilityDatabase
- Add-SqlAvailabilityDatabase
- Suspend-SqlAvailabilityDatabase
- New-SqlAvailabilityGroup
- Set-SqlAvailabilityGroup
- Remove-SqlAvailabilityGroup
- Switch-SqlAvailabilityGroup
- Join-SqlAvailabilityGroup
- Revoke-SqlAvailabilityGroupCreateAnyDatabase
- Grant-SqlAvailabilityGroupCreateAnyDatabase
- New-SqlAvailabilityGroupListener
- Set-SqlAvailabilityGroupListener
- Add-SqlAvailabilityGroupListenerStaticIp
- Set-SqlAvailabilityReplica
- Remove-SqlAvailabilityReplica
- New-SqlAvailabilityReplica
- Set-SqlAvailabilityReplicaRoleToSecondary
- New-SqlBackupEncryptionOption
- Get-SqlBackupHistory
- Invoke-Sqlcmd
- New-SqlCngColumnMasterKeySettings
- Remove-SqlColumnEncryptionKey
- Get-SqlColumnEncryptionKey
- Remove-SqlColumnEncryptionKeyValue
- Add-SqlColumnEncryptionKeyValue
- Get-SqlColumnMasterKey
- Remove-SqlColumnMasterKey
- New-SqlColumnMasterKey
- Get-SqlCredential
- Set-SqlCredential
- New-SqlCredential
- Remove-SqlCredential
- New-SqlCspColumnMasterKeySettings
- Get-SqlDatabase
- Restore-SqlDatabase
- Backup_SqlDatabase
- Set-SqlErrorLog
- Get-SqlErrorLog
- New-SqlHADREndpoint
- Set-SqlHADREndpoint
- Get-SqlInstance
- Add-SqlLogin
- Remove-SqlLogin
- Get-SqlLogin
- Set-SqlSmartAdmin
- Get-SqlSmartAdmin
- Read-SqlTableData
- Write-SqlTableData
- Read-SqlViewData
- Convert-UrnToPath

## <a name="see-also"></a>Siehe auch
- [SQL Server-PowerShell](../relational-databases/scripting/sql-server-powershell.md)
