---
title: Verwalten von SQLServer unter Linux mit PowerShell | Microsoft-Dokumentation
description: Dieser Artikel enthält einen Überblick über die mithilfe von PowerShell unter Windows mit SQL Server unter Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 8398db9e03aabf6863bd770f8be6657b58be1591
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718076"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Verwalten von SQLServer unter Linux mithilfe von PowerShell unter Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel werden [SQL Server PowerShell](../powershell/sql-server-powershell.md) und führt Sie durch einige Beispiele zur Verwendung mit SQL Server unter Linux verwenden. PowerShell-Unterstützung für SQL Server ist derzeit verfügbar für Windows, MacOS und Linux. Dieser Artikel führt Sie durch die Verwendung eines Windows-Computers für die Verbindung zu einer Remoteinstanz von SQL Server unter Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Installieren Sie die neueste Version von SQL PowerShell unter Windows

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) unter Windows wird im PowerShell-Katalog verwaltet. Bei der Arbeit mit SQL Server sollten Sie immer die neueste Version des SqlServer PowerShell-Moduls verwenden.

## <a name="before-you-begin"></a>Vorbereitungen

Lesen der [bekannte Probleme](sql-server-linux-release-notes.md) für SQLServer unter Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Starten Sie PowerShell, und importieren Sie die *Sqlserver* Modul

Beginnen wir mit PowerShell unter Windows starten. Verwendung <kbd>gewinnen</kbd>+<kbd>R</kbd>, auf den Windows-Computer, und geben **PowerShell** um eine neue Windows PowerShell-Sitzung zu starten.

```
PowerShell
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

Lassen Sie uns mithilfe von PowerShell in Windows eine Verbindung mit Ihrer SQL Server-Instanz unter Linux herstellen und eine Reihe von Servereigenschaften anzuzeigen.

Kopieren Sie die folgenden Befehle an der PowerShell-Eingabeaufforderung. Wenn Sie diese Befehle ausführen, wird PowerShell aus:
- Ein Dialogfeld, das Sie, für den Hostnamen oder IP-Adresse der Instanz auffordert angezeigt
- Anzeigen der *Windows PowerShell anmelden* Dialogfeld, in dem Sie die Anmeldeinformationen dazu aufgefordert werden. Sie können Ihrer *SQL-Benutzernamen* und *SQL-Kennwort* zur Verbindung mit Ihrer SQL Server-Instanz unter Linux
- Verwenden der **Get-SqlInstance** -Cmdlet zum Herstellen einer Verbindung mit der **Server** und einige Eigenschaften anzeigen

Optional können Sie einfach ersetzen die `$serverInstance` Variable mit dem die IP-Adresse oder den Hostnamen Ihrer SQL Server-Instanz.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Connect to the Server and get a few properties
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

Eine weitere Option für die Verbindung mit Ihrer SQL Server-Instanz ist die Verwendung der [SQL Server PowerShell Provider](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider).  Dieser Anbieter können Sie SQL Server-Instanz, die ähnlich wie wenn Sie die Baumstruktur im Objekt-Explorer, sondern auf der Befehlszeile navigiert wurden navigieren.  Dieser Anbieter wird standardmäßig als ein PSDrive, das mit dem Namen angezeigt `SQLSERVER:\` die Sie verwenden können, zu verbinden, und navigieren SQL Server-Instanzen, die Ihr Domänenkonto Zugriff hat.  Finden Sie unter [Konfigurationsschritte](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps) für Informationen zum Einrichten von Active Directory-Authentifizierung für SQL Server unter Linux.

Sie können auch SQL-Authentifizierung mit SQL Server PowerShell-Anbieter verwenden. Verwenden Sie hierzu die `New-PSDrive` Cmdlet erstellen ein neues PSDrive, und geben Sie die richtigen Anmeldeinformationen, um eine Verbindung herzustellen.

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

Hier ist die Ausgabe könnte folgendermaßen aussehen.  Sie werden feststellen, dass die Ausgabe ähnelt der was SSMS auf den Knoten "Datenbanken" angezeigt wird.  Es zeigt die Benutzerdatenbanken, jedoch nicht in den Systemdatenbanken.

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

Wenn Sie alle Datenbanken in Ihrer Instanz angezeigt müssen, eine Möglichkeit ist die Verwendung der [Get-SqlDatabase](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlDatabase) Cmdlet.

## <a name="examine-sql-server-error-logs"></a>SQL Server-Fehlerprotokollen

Die folgenden Schritte mithilfe von PowerShell unter Windows um Fehler zu untersuchen, die Protokolle, die auf Ihre SQL Server-Instanz unter Linux eine Verbindung her. Wir verwenden auch die **Out-GridView** -Cmdlet zum Anzeigen von Informationen aus den Fehler protokolliert wird, im Raster Ansicht anzuzeigen.

Kopieren Sie die folgenden Befehle an der PowerShell-Eingabeaufforderung. Sie können einige Minuten dauern. Diese Befehle wie folgt vor:
- Ein Dialogfeld, das Sie, für den Hostnamen oder IP-Adresse der Instanz auffordert angezeigt
- Anzeigen der *Windows PowerShell anmelden* Dialogfeld, in dem Sie die Anmeldeinformationen dazu aufgefordert werden. Sie können Ihrer *SQL-Benutzernamen* und *SQL-Kennwort* zur Verbindung mit Ihrer SQL Server-Instanz unter Linux
- Verwenden der **Get-SqlErrorLog** Cmdlet, um eine Verbindung mit SQL Server-Instanz unter Linux herstellen und Abrufen von Fehler protokolliert, da **gestern**
- Die Ausgabe an die **Out-GridView** Cmdlet

Optional können Sie ersetzen die `$serverInstance` Variable mit dem die IP-Adresse oder den Hostnamen Ihrer SQL Server-Instanz.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>Siehe auch
- [SQL Server-PowerShell](../relational-databases/scripting/sql-server-powershell.md)
- [SqlServer-Cmdlets](https://docs.microsoft.com/powershell/module/sqlserver)
