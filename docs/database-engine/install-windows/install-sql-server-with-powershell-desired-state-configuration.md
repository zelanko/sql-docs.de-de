---
title: Installieren von SQL Server mit PowerShell Desired State Configuration | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Installation von SQL Server mit PowerShell Desired State Configuration (DSC).
ms.custom: ''
ms.date: 10/26/2018
ms.devlang: PowerShell
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
author: randomnote1
ms.author: dareist
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 16d425d8eb66a950f432fa3ef9c68a8e68a78d22
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148478"
---
# <a name="install-sql-server-with-powershell-desired-state-configuration"></a>Installieren von SQL Server mit PowerShell Desired State Configuration

Wie oft haben Sie sich mit den gewohnten Schaltflächen durch die Installationsoberfläche von SQL Server geklickt und die gewohnten Informationen eingegeben, ohne darüber nachzudenken? Nach der Installation stellen Sie dann fest, dass Sie vergessen haben, die DBA-Gruppe in der Rolle des Systemadministrators zu erstellen. Nun müssen Sie wertvolle Zeit investieren, um zum Einzelbenutzermodus zu wechseln und die entsprechenden Benutzer oder Gruppen hinzuzufügen, SQL wieder in den Mehrbenutzermodus zu versetzen und die Änderungen zu testen. Noch schlimmer ist jedoch, dass Sie nun die gesamte Installation in Frage stellen. „Was habe ich noch vergessen?“ Ich war schon mehr als einmal in dieser Situation.

Verwenden Sie [PowerShell Desired State Configuration (DSC)](https://docs.microsoft.com/powershell/dsc/overview). Mithilfe von DSC können Sie eine Konfigurationsvorlage erstellen, die für zahlreiche Server wiederverwendet werden kann. Je nach Build müssen eine Setupparameter angepasst werden. Das ist jedoch kein großer Aufwand, da die Standardeinstellungen trotzdem beibehalten werden können. Der Vorteil besteht darin, dass Sie nicht vergessen können, einen wichtigen Parameter einzugeben.

In diesem Artikel wird das Setup einer eigenständigen Instanz von SQL Server 2017 unter Windows Server 2016 mithilfe der DSC-Ressource „SqlServerDsc“ erläutert. Es wird nicht erläutert, wie DSC funktioniert, deshalb sind DSC-Grundkenntnisse von Vorteil.

Folgendes ist für diese exemplarische Vorgehensweise erforderlich:

- Ein Computer, auf dem Windows Server 2016 ausgeführt wird
- Ein Installationsmedium für SQL Server 2017
- Die DSC-Ressource „SqlServerDsc“ (Version 10.0.0.0 war das aktuelle Release, als dieser Artikel verfasst wurde)

## <a name="prerequisites"></a>Voraussetzungen

In den meisten Fällen wird DSC verwendet, um die erforderlichen Voraussetzungen zu erfüllen. Zur Veranschaulichung werden die Voraussetzungen in diesem Artikel jedoch manuell verarbeitet.

## <a name="install-the-sqlserverdsc-dsc-resource"></a>Installieren der DSC-Ressource „SqlServerDsc“

Die DSC-Ressource [SqlServerDsc](https://www.powershellgallery.com/packages/SqlServerDsc) kann mithilfe des Cmdlets [Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module?view=powershell-5.1) aus dem [PowerShell-Katalog](https://www.powershellgallery.com/) heruntergeladen werden. _Hinweis: Achten Sie darauf, dass PowerShell als Administrator ausgeführt wird, wenn Sie das Modul installieren möchten._

```PowerShell
Install-Module -Name SqlServerDsc
```

Herunterladen des Installationsmediums für SQL Server 2017 Laden Sie das Installationsmedium für SQL Server 2017 auf den Server herunter. In diesem Fall wurde SQL Server 2017 Enterprise aus einem Visual Studio-Abonnement heruntergeladen, und die ISO-Datei wurde nach „C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso“ kopiert.

Nun muss die ISO-Datei in ein Verzeichnis extrahiert werden.

```PowerShell
New-Item -Path C:\SQL2017 -ItemType Directory
$mountResult = Mount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso' -PassThru
$volumeInfo = $mountResult | Get-Volume
$driveInfo = Get-PSDrive -Name $volumeInfo.DriveLetter
Copy-Item -Path ( Join-Path -Path $driveInfo.Root -ChildPath '*' ) -Destination C:\SQL2017\ -Recurse
Dismount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso'
```

## <a name="create-the-configuration"></a>Erstellen der Konfiguration

### <a name="configuration"></a>Konfiguration

Erstellen Sie die Konfigurationsfunktion, die aufgerufen wird, um die [MOF-Dokumente (Managed Object Format)](https://docs.microsoft.com/windows/desktop/WmiSdk/managed-object-format--mof-) zu generieren.

```PowerShell
Configuration SQLInstall
{...}
```

### <a name="modules"></a>Module

Importieren Sie die Module in die aktuelle Sitzung. Diese Module teilen dem Konfigurationsdokument mit, wie die MOF-Dokumente erstellt werden sollen, und der DSC-Engine, wie die MOF-Dokumente auf den Server angewendet werden sollen.

```PowerShell
Import-DscResource -ModuleName SqlServerDsc
```

### <a name="resources"></a>Ressourcen

#### <a name="net-framework"></a>.NET Framework

SQL Server basiert auf .NET Framework. Deshalb muss .NET Framework installiert sein, bevor SQL Server installiert wird. Die Ressource „WindowsFeature“ wird verwendet, um das Feature „Net-Framework-45-Core“ zu installieren.

```PowerShell
WindowsFeature 'NetFramework45'
{
     Name = 'Net-Framework-45-Core'
     Ensure = 'Present'
}
```

#### <a name="sqlsetup"></a>SqlSetup

Die Ressource „SqlSetup“ wird verwendet, um DSC mitzuteilen, wie SQL Server installiert werden soll. Folgende Parameter sind für eine Basisinstallation erforderlich:

- **InstanceName:** Der Name der Instanz. Verwenden Sie „MSSQLSERVER“ als Standardinstanz.
- **Features:** Die zu installierenden Features. In diesem Beispiel wird nur das Feature „SQLEngine“ installiert.
- **SourcePath:** Der Pfad zum Installationsmedium für SQL Server. In diesem Fall wurde das Installationsmedium für SQL Server unter „C:\SQL2017“ gespeichert. Eine Netzwerkfreigabe kann verwendet werden, um den Speicherplatz zu minimieren, der auf dem Server verwendet wird.
- **SQLSysAdminAccounts:** Die Benutzer oder Gruppen, die Mitglieder in der Rolle „Systemadministrator“ sein sollen. In diesem Beispiel werden der lokalen Gruppe „Administrators“ Systemadministratorrechte erteilt. _Hinweis: Diese Konfiguration wird in einer Umgebung mit hoher Sicherheit nicht empfohlen._

Eine vollständige Liste mit Beschreibungen der Parameter, die für „SqlSetup“ verfügbar sind, ist im [GitHub-Repository „SqlServerDsc“](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlsetup) verfügbar.

Die Ressource „SqlSetup“ ist nicht ideal, da es nur SQL Server installiert und die angewendeten Einstellungen dabei nicht beibehält. Wenn die Systemadministratoren beispielsweise zur Installationszeit definiert werden, könnte ein Administrator Konten zur Rolle hinzufügen oder aus dieser entfernen, ohne dass die Ressource „SqlSetup“ dies beachtet. Wenn DSC die Mitgliedschaft in der Systemadministratorrolle erzwingen soll, sollte die Ressource [SqlServerRole](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlserverrole) verwendet werden.

#### <a name="complete-configuration"></a>Vollständige Konfiguration

```PowerShell
Configuration SQLInstall
{
     Import-DscResource -ModuleName SqlServerDsc

     node localhost
     {
          WindowsFeature 'NetFramework45'
          {
               Name   = 'NET-Framework-45-Core'
               Ensure = 'Present'
          }

          SqlSetup 'InstallDefaultInstance'
          {
               InstanceName        = 'MSSQLSERVER'
               Features            = 'SQLENGINE'
               SourcePath          = 'C:\SQL2017'
               SQLSysAdminAccounts = @('Administrators')
               DependsOn           = '[WindowsFeature]NetFramework45'
          }
     }
}
```

## <a name="build-and-deploy"></a>Erstellen und Bereitstellen

### <a name="compile-the-configuration"></a>Kompilieren der Konfiguration

Stellen Sie dem Pfad des Konfigurationsskripts einen Punkt voran, damit es im selben Gültigkeitsbereich ausgeführt werden kann:

```PowerShell
. .\SQLInstallConfiguration.ps1
```

Führen Sie die Konfigurationsfunktion aus:

```PowerShell
SQLInstall
```

Im Arbeitsverzeichnis namens „SQLInstall“ wird ein Verzeichnis erstellt, das eine Datei namens „localhost.mof“ enthält. Wenn Sie den Inhalt der MOF-Datei überprüfen, wird die kompilierte DSC-Konfiguration angezeigt.

### <a name="deploy-the-configuration"></a>Bereitstellen der Konfiguration

Rufen Sie das Cmdlet „Start-DscConfiguration“ auf, um die DSC-Bereitstellung von SQL Server zu starten. Folgende Parameter werden im Cmdlet verwendet:

- **-Path:** Der Pfad zum Ordner, der die bereitzustellenden MOF-Dokumente enthält (z.B. „C:\SQLInstall“).
- **-Wait:** Legt fest, dass auf den Abschluss des Konfigurationsauftrags gewartet werden soll.
- **-Force:** Legt fest, dass vorhandene DSC-Konfigurationen überschrieben werden sollen.
- **-Verbose:** Zeigt die Ausgabe ausführlich an. Dies ist hilfreich, wenn Sie eine Konfiguration zur Problembehandlung zum ersten Mal mithilfe von Push übertragen.

```PowerShell
Start-DscConfiguration -Path C:\SQLInstall -Wait -Force -Verbose
```

Wenn die Konfiguration angewendet wurde, zeigt die ausführliche Ausgabe an, was geschieht. Solange keine Fehler (roter Text) angezeigt werden, wenn „Operation 'Invoke CimMethod' complete.“ auf dem Bildschirm angezeigt wird, sollte SQL Server installiert sein.

## <a name="validate-installation"></a>Überprüfen der Installation

### <a name="dsc"></a>DSC

Das Cmdlet [Test-DscConfiguration](https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration) kann verwendet werden, um zu ermitteln, ob der aktuelle Zustand des Servers, in diesem Fall die Installation von SQL Server, dem gewünschten Zustand entspricht. Das Ergebnis von „Test-DscConfiguration“ sollte „True“ sein.

```PowerShell
PS C:\> Test-DscConfiguration
True
```

### <a name="services"></a>Dienste

Wenn Sie die Dienste auflisten, sollten nun die SQL Server-Dienste aufgeführt werden.

```PowerShell
PS C:\> Get-Service -Name *SQL*
Status  Name           DisplayName
------  ----           -----------
Running MSSQLSERVER    SQL Server (MSSQLSERVER)
Stopped SQLBrowser     SQL Server Browser
Running SQLSERVERAGENT SQL Server Agent (MSSQLSERVER)
Running SQLTELEMETRY   SQL Server CEIP service (MSSQLSERVER)
Running SQLWriter      SQL Server VSS Writer
```

### <a name="sql-server"></a>SQL Server

```PowerShell
PS C:\> & sqlcmd -S $env:COMPUTERNAME
1> SELECT @@SERVERNAME
2> GO
1> quit
```

## <a name="see-also"></a>Siehe auch

[Windows PowerShell DSC – Übersicht](https://docs.microsoft.com/powershell/dsc/overview)

[Installieren von SQL Server von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)

[Installieren von SQL Server mithilfe einer Konfigurationsdatei](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)
