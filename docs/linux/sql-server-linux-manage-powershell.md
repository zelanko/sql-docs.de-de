---
title: Verwalten von SQLServer unter Linux mit PowerShell | Microsoft-Dokumentation
description: Dieser Artikel enthält einen Überblick über die mithilfe von PowerShell unter Windows mit SQL Server unter Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: b9b8429bfdc1738955aba739520ac07e2d39efa7
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712082"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Verwalten von SQLServer unter Linux mithilfe von PowerShell unter Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel werden [SQL Server PowerShell](https://msdn.microsoft.com/library/mt740629.aspx) und führt Sie durch einige Beispiele zur Verwendung mit SQL Server unter Linux verwenden. PowerShell-Unterstützung für SQL Server steht derzeit für Windows, damit Sie sie verwenden können, wenn Sie einen Windows-Computer verfügen, der zu einer Remoteinstanz von SQL Server unter Linux eine Verbindung herstellen können.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Installieren Sie die neueste Version von SQL PowerShell unter Windows

[SQL PowerShell](https://msdn.microsoft.com/library/mt740629.aspx) für Windows ist im Lieferumfang [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md). Bei der Arbeit mit SQL Server sollten Sie immer die neueste Version von SSMS und SQL PowerShell verwenden. Die neueste Version von SSMS wird ständig aktualisiert und optimiert und arbeitet zurzeit mit SQL Server unter Linux. Zum Herunterladen und installieren die neueste Version, finden Sie unter [Herunterladen von SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Um auf dem neuesten Stand zu bleiben, die neueste Version von SSMS werden Sie aufgefordert, wenn eine neue Versionen zum download zur Verfügung.

## <a name="before-you-begin"></a>Vorbereitungen

Lesen der [bekannte Probleme](sql-server-linux-release-notes.md) für SQLServer unter Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Starten Sie PowerShell, und importieren Sie die *Sqlserver* Modul

Beginnen wir mit PowerShell unter Windows starten. Öffnen einer *Eingabeaufforderung* auf den Windows-Computer, und geben **PowerShell** um eine neue Windows PowerShell-Sitzung zu starten.

```
PowerShell
```

SQL Server bietet ein Windows PowerShell-Modul, das mit dem Namen **SqlServer** , dass Sie zum Importieren von SQL Server-Komponenten (SQL Server-Anbieter und Cmdlets) in einer PowerShell-Umgebung oder einem Skript verwenden können.

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
Script     0.0        SqlServer
Manifest   20.0       SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Verbinden mit SQL Server, und erhalten Sie Informationen zum server

Lassen Sie uns mithilfe von PowerShell in Windows eine Verbindung mit Ihrer SQL Server-Instanz unter Linux herstellen und eine Reihe von Servereigenschaften anzuzeigen.

Kopieren Sie die folgenden Befehle an der PowerShell-Eingabeaufforderung. Wenn Sie diese Befehle ausführen, wird PowerShell aus:
- Anzeigen der *Windows PowerShell anmelden* Dialogfeld, das Sie für die Anmeldeinformationen aufgefordert werden (*SQL-Benutzernamen* und *SQL-Kennwort*) für die Verbindung mit SQL Server -Instanz unter Linux
- Laden Sie die Assembly für die SQL Server Management Objects (SMO)
- Erstellen Sie eine Instanz von der [Server](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.server.aspx) Objekt
- Herstellen einer Verbindung mit der **Server** und einige Eigenschaften anzeigen

Ersetzen Sie **\<Your_server_instance\>** mit der IP-Adresse oder den Hostnamen Ihrer SQL Server-Instanz unter Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Load the SMO assembly and create a Server object
[System.Reflection.Assembly]::LoadWithPartialName('Microsoft.SqlServer.SMO') | out-null
$server = New-Object ('Microsoft.SqlServer.Management.Smo.Server') $serverInstance

# Set credentials
$server.ConnectionContext.LoginSecure=$false
$server.ConnectionContext.set_Login($credential.UserName)
$server.ConnectionContext.set_SecurePassword($credential.Password)

# Connect to the Server and get a few properties
$server.Information | Select-Object Edition, HostPlatform, HostDistribution | Format-List
# done
```

PowerShell sollte Informationen ähnlich wie die folgende Ausgabe angezeigt werden:

```
Edition          : Developer Edition (64-bit)
HostPlatform     : Linux
HostDistribution : Ubuntu
```
> [!NOTE]
> Wenn nichts für diese Werte angezeigt wird, konnte die Verbindung mit der SQL Server-Zielinstanz in den meisten Fällen nicht. Stellen Sie sicher, dass Sie dieselben Verbindungsinformationen für die Verbindung von SQL Server Management Studio verwenden können. Überprüfen Sie anschließend die [Empfehlungen zur Verbindungsproblembehandlung](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="examine-sql-server-error-logs"></a>SQL Server-Fehlerprotokollen

Verwenden von PowerShell unter Windows, überprüfen Sie die Fehlerprotokolle auf Ihre SQL Server-Instanz unter Linux uns in Verbindung. Wir verwenden auch die **Out-GridView** -Cmdlet zum Anzeigen von Informationen aus den Fehler protokolliert wird, im Raster Ansicht anzuzeigen.

Kopieren Sie die folgenden Befehle an der PowerShell-Eingabeaufforderung. Sie können einige Minuten dauern. Diese Befehle wie folgt vor:
- Anzeigen der *Windows PowerShell anmelden* Dialogfeld, das Sie für die Anmeldeinformationen aufgefordert werden (*SQL-Benutzernamen* und *SQL-Kennwort*) für die Verbindung mit SQL Server -Instanz unter Linux
- Verwenden der **Get-SqlErrorLog** Cmdlet, um eine Verbindung mit SQL Server-Instanz unter Linux herstellen und Abrufen von Fehler protokolliert, da **gestern**
- Die Ausgabe an die **Out-GridView** Cmdlet

Ersetzen Sie **\<Your_server_instance\>** mit der IP-Adresse oder den Hostnamen Ihrer SQL Server-Instanz unter Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>Siehe auch
- [SQL Server-PowerShell](../relational-databases/scripting/sql-server-powershell.md)
