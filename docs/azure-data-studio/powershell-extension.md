---
title: PowerShell-Erweiterung
titleSuffix: Azure Data Studio
description: Installieren und Verwenden von PowerShell für Azure Data Studio
ms.custom: seodec18
ms.date: 04/19/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
manager: matthend
ms.openlocfilehash: 72c4d64cc93ab564b9b8b04a838f8226982890f0
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257577"
---
# <a name="powershell-editor-support-for-azure-data-studio"></a>PowerShell-Editor-Unterstützung für Azure Data Studio

Diese Erweiterung bietet umfassende Unterstützung für den PowerShell-Editor in [Azure Data Studio](https://github.com/Microsoft/azuredatastudio).
Jetzt können Sie PowerShell-Skripts mit der ausgezeichneten IDE-ähnlichen Schnittstelle schreiben und debuggen, die Azure Data Studio bereitstellt.

![PowerShell-Erweiterung](media/powershell-extension/powershell-extension.png)


## <a name="features"></a>Features

- Syntaxhervorhebung
- Codeausschnitte
- IntelliSense für Cmdlets und mehr
- Von [PowerShell Script Analyzer](http://github.com/PowerShell/PSScriptAnalyzer) bereitgestellte regelbasierte Analyse
- „Gehe zu Definition“ von Cmdlets und Variablen
- „Verweise suchen“ von Cmdlets und Variablen
- Ermittlung von Dokument- und Arbeitsbereichssymbolen
- Auswahl von „Ausgewählte ausführen“ in PowerShell-Code mithilfe von <kbd>F8</kbd>
- Starten der Onlinehilfe für das Symbol unter dem Cursor mithilfe von <kbd>STRG</kbd>+<kbd>F1</kbd>
- Grundlegende interaktive Konsolenunterstützung!


## <a name="installing-the-extension"></a>Installieren der Erweiterung

Sie können das offizielle Release der PowerShell-Erweiterung installieren, indem Sie die Schritte in der [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/extensions)-Dokumentation ausführen.
Suchen Sie im Bereich „Erweiterungen“ nach der Erweiterung „PowerShell“, und installieren Sie sie dort.  Sie werden automatisch über alle zukünftigen Updates der Erweiterung benachrichtigt.

Sie können auch ein VSIX-Paket von unserer Seite [Releases](https://github.com/PowerShell/vscode-powershell/releases) herunterladen und über die Befehlszeile installieren:

```powershell
azuredatastudio --install-extension PowerShell-<version>.vsix
```

## <a name="platform-support"></a>Plattformunterstützung

- **Windows 7 bis 10** mit Windows PowerShell V3 und höher und PowerShell Core
- **Linux** mit PowerShell Core (alle von PowerShell unterstützten Distributionen)
- **macOS** mit PowerShell Core

In den [FAQ](https://github.com/PowerShell/vscode-powershell/wiki/FAQ) finden Sie Antworten auf häufig gestellte Fragen.

## <a name="installing-powershell-core"></a>Installieren von PowerShell Core

Wenn Sie Azure Data Studio unter macOS oder Linux ausführen, müssen Sie möglicherweise auch PowerShell Core installieren.

PowerShell Core ist ein Open-Source-Projekt auf [GitHub](https://github.com/powershell/powershell).
Weitere Informationen zur Installation von PowerShell Core auf macOS- oder Linux-Plattformen finden Sie in den folgenden Artikeln:

- [Installieren von PowerShell Core unter Linux](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [Installieren von PowerShell Core unter macOS](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)

## <a name="example-scripts"></a>Beispielskripts

Im `examples`-Ordner der Erweiterung finden Sie einige Beispielskripts, mit denen Sie die PowerShell-Funktionen zum Bearbeiten und Debuggen erkunden können.  Weitere Informationen zur Verwendung finden Sie in der enthaltenen [README.md](https://github.com/PowerShell/vscode-powershell/blob/master/examples/README.md)-Datei.

Dieser Ordner befindet sich im folgenden Pfad:

```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.PowerShell-<version>/examples
```

Wenn Sie die Vorschauversion der Erweiterung verwenden, befindet sich der Ordner hier:

 ```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.powershell-preview-<version>/examples
```

Um die Beispiele der Erweiterung in Azure Data Studio zu öffnen und anzuzeigen, führen Sie den folgenden Code an der PowerShell-Eingabeaufforderung aus:

```powershell
azuredatastudio (Get-ChildItem $Home\.azuredatastudio\extensions\ms-vscode.PowerShell-*\examples)[-1]
```

### <a name="creating-and-opening-files"></a>Erstellen und Öffnen von Dateien

Um im Editor eine neue Datei zu erstellen und zu öffnen, verwenden Sie den Befehl „New-EditorFile“ im integrierten PowerShell-Terminal.

```powershell
PS C:\temp> New-EditorFile ExportData.ps1
```

Dieser Befehl funktioniert für jeden Dateityp, nicht nur für PowerShell-Dateien.

```powershell
PS C:\temp> New-EditorFile ImportData.py
```

Um eine oder mehrere Dateien in Azure Data Studio zu öffnen, verwenden Sie den Befehl `Open-EditorFile`.

```powershell
Open-EditorFile ExportData.ps1, ImportData.py
```

### <a name="no-focus-on-console-when-executing"></a>Kein Fokus auf der Konsole beim Ausführen

Wenn Sie häufiger mit SSMS arbeiten, kennen Sie das: Sie können eine bereits ausgeführte Abfrage erneut ausführen, ohne zuvor zum Abfragebereich zurückkehren zu müssen.  In diesem Fall kommt Ihnen das Standardverhalten des Code-Editors möglicherweise etwas fremd vor.  Um den Fokus im Editor beizubehalten, wenn Sie den Code mit <kbd>F8</kbd> ausführen, ändern Sie die folgende Einstellung:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Der Standardwert lautet aus Gründen der Barrierefreiheit `true`.

Beachten Sie, dass diese Einstellung verhindert, dass der Fokus zur Konsole wechselt, auch wenn Sie einen Befehl verwenden, der explizit eine Eingabe erfordert, wie z.B. `Get-Credential`.

## <a name="sql-powershell-examples"></a>SQL-PowerShell-Beispiele
Um diese Beispiele (unten) verwenden zu können, müssen Sie das Modul „SqlServer“ aus dem [PowerShell-Katalog](https://www.powershellgallery.com/packages/SqlServer) installieren.

```powershell
Install-Module -Name SqlServer
```

> [!NOTE]
> Ab Version `21.1.18102` unterstützt das `SqlServer`-Modul zusätzlich zu Windows PowerShell auch [PowerShell Core 6.2](https://github.com/PowerShell/PowerShell) und höher.

In diesem Beispiel wird das `Get-SqlInstance`-Cmdlet verwendet, um die Server-SMO-Objekte für ServerA und ServerB abzurufen.  Die Standardausgabe für diesen Befehl enthält den Instanznamen, die Version, das Service Pack und die CU-Updateebene der Instanzen.

```powershell
Get-SqlInstance -ServerInstance ServerA, ServerB
```

Die Ausgabe sieht ähnlich wie das folgende Beispiel aus:

```
Instance Name             Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------             -------    ------------ -----------  ------------ ----------------
ServerA                   13.0.5233  SP2          CU4          Windows      Windows Server 2016 Datacenter
ServerB                   14.0.3045  RTM          CU12         Linux        Ubuntu
```
Das `SqlServer`-Modul enthält einen Anbieter namens `SQLRegistration`, mit dem Sie programmgesteuert auf die folgenden Arten gespeicherter SQL Server-Verbindungen zugreifen können:

+ Datenbank-Engine-Server (registrierte Server)
+ Zentraler Verwaltungsserver
+ Analysis Services
+ Integration Services
+ Reporting Services

 Im folgenden Beispiel wird mit `dir` (einem Alias für `Get-ChildItem`) die Liste aller SQL Server-Instanzen abgerufen, die in der Datei mit den registrierten Servern aufgeführt sind.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse 
```

Die Ausgabe sieht ähnlich wie das folgende Beispiel aus:

```powershell
Mode Name
---- ----
-    ServerA
-    ServerB
-    localhost\SQL2017
-    localhost\SQL2016Happy
-    localhost\SQL2017
```

Bei vielen Vorgängen, die eine Datenbank oder Objekte in einer Datenbank einbeziehen, kann das Cmdlet `Get-SqlDatabase` verwendet werden.  Wenn Sie Werte für den `-ServerInstance`-Parameter und den `-Database`-Parameter angeben, wird nur dieses Datenbankobjekt abgerufen.  Wenn Sie jedoch nur den `-ServerInstance`-Parameter angeben, wird eine vollständige Liste aller Datenbanken in dieser Instanz zurückgegeben.

Die Ausgabe sieht ähnlich wie das folgende Beispiel aus:

```
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2017   Normal      336.00 MB   57.01 MB Simple       140 sa
master               Normal        6.00 MB  368.00 KB Simple       140 sa
model                Normal       16.00 MB    5.53 MB Full         140 sa
msdb                 Normal       48.44 MB    1.70 MB Simple       140 sa
PBIRS                Normal      144.00 MB   55.95 MB Full         140 sa
PBIRSTempDB          Normal       16.00 MB    4.20 MB Simple       140 sa
SSISDB               Normal      325.06 MB   26.21 MB Full         140 sa
tempdb               Normal       72.00 MB   61.25 MB Simple       140 sa
WideWorldImporters   Normal         3.2 GB     2.6 GB Simple       130 sa
```

Im nächsten Beispiel wird mit dem Cmdlet `Get-SqlDatabase` eine Liste aller Datenbanken auf der Instanz „ServerB“ abgerufen. Anschließend wird (mithilfe des Cmdlets `Out-GridView`) ein Raster bzw. eine Tabelle dargestellt, in dem bzw. der Sie auswählen können, welche Datenbanken gesichert werden sollen.  Sobald der Benutzer auf die Schaltfläche „OK“ klickt, werden nur die markierten Datenbanken gesichert.

```powershell
Get-SqlDatabase -ServerInstance ServerB |
Out-GridView -PassThru |
Backup-SqlDatabase -CompressionOption On
```

In diesem Beispiel wird wiederum eine Liste aller SQL Server-Instanzen abgerufen, die in der Datei mit registrierten Servern aufgeführt sind. Anschließend wird das `Get-SqlAgentJobHistory`-Element abgerufen, das jeden fehlerhaften SQL Agent-Auftrag seit Mitternacht für jede aufgeführte SQL Server-Instanz meldet.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE {$_.Mode -ne 'd' } |
FOREACH {
    Get-SqlAgentJobHistory -ServerInstance  $_.Name -Since Midnight -OutcomesType Failed
}
```

Im folgenden Beispiel wird zunächst mit `dir` (einem Alias für `Get-ChildItem`) die Liste aller SQL Server-Instanzen abgerufen, die in der Datei „Registrierte Server“ aufgeführt sind. Danach rufen wir mit dem Cmdlet `Get-SqlDatabase` eine Liste mit Datenbanken für jede dieser Instanzen ab.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE { $_.Mode -ne 'd' } |
FOREACH {
    Get-SqlDatabase -ServerInstance $_.Name
}
```

Die Ausgabe sieht ähnlich wie das folgende Beispiel aus:

```
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level      
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2017   Normal      336.00 MB   57.01 MB Simple       140 sa   
master               Normal        6.00 MB  368.00 KB Simple       140 sa   
model                Normal       16.00 MB    5.53 MB Full         140 sa   
msdb                 Normal       48.44 MB    1.70 MB Simple       140 sa   
PBIRS                Normal      144.00 MB   55.95 MB Full         140 sa   
PBIRSTempDB          Normal       16.00 MB    4.20 MB Simple       140 sa   
SSISDB               Normal      325.06 MB   26.21 MB Full         140 sa   
tempdb               Normal       72.00 MB   61.25 MB Simple       140 sa   
WideWorldImporters   Normal         3.2 GB     2.6 GB Simple       130 sa   
```

## <a name="reporting-problems"></a>Melden von Problemen

Wenn Probleme mit der PowerShell-Erweiterung auftreten, finden Sie in der [Dokumentation zur Problembehandlung](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md) Informationen zum Diagnostizieren und Melden von Problemen.

#### <a name="security-note"></a>Sicherheitshinweis

Informationen zu Sicherheitsproblemen finden Sie [hier.](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md#note-on-security)

## <a name="contributing-to-the-code"></a>Mitwirken am Code

Informationen dazu, wie Sie an dieser Erweiterung mitwirken können, finden Sie in der [Dokumentation zur Entwicklung](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md).

## <a name="maintainers"></a>Maintainer

- [Keith Hill](https://github.com/rkeithhill) - [@r_keith_hill](http://twitter.com/r_keith_hill)
- [Tyler Leonhardt](https://github.com/tylerl0706) - [@TylerLeonhardt](http://twitter.com/tylerleonhardt)
- [Rob Holt](https://github.com/rjmholt)

## <a name="license"></a>Lizenz

Diese Erweiterung ist [unter der MIT-Lizenz lizenziert](https://github.com/PowerShell/vscode-powershell/blob/master/LICENSE.txt). Informationen zu den Binärdateien von Drittanbietern, die in Releases dieses Projekts enthalten sind, finden Sie in der Datei mit [Hinweisen zu Drittanbietern](https://github.com/PowerShell/vscode-powershell/blob/master/Third%20Party%20Notices.txt).

## <a name="code-of-conductconduct-md"></a>[Verhaltensregeln][conduct-md]

Für dieses Projekt gelten die Microsoft-Verhaltensregeln für Open Source ([Microsoft Open Source Code of Conduct][conduct-code]).
Um weitere Informationen zu erhalten, lesen Sie die häufig gestellten Fragen zu den Verhaltensregeln ([Code of Conduct FAQ][conduct-FAQ]), oder wenden Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com][conduct-email].

[conduct-code]: https://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: https://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
