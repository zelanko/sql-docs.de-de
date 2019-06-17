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
ms.openlocfilehash: c7a2dbdccf92a52d5733a04915acc3f76dc3f033
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105948"
---
# <a name="powershell-editor-support-for-azure-data-studio"></a>PowerShell-Editor-Unterstützung für Azure Data Studio

Diese Erweiterung bietet umfassende PowerShell-Editor-Unterstützung in [Studio für Azure Data](https://github.com/Microsoft/azuredatastudio).
Jetzt können Sie schreiben und Debuggen von PowerShell-Skripts, die mithilfe der ausgezeichneten IDE-ähnliche-Schnittstelle, die Azure Data Studio bereitstellt.

![PowerShell-Erweiterung](media/powershell-extension/powershell-extension.png)


## <a name="features"></a>Features

- Syntaxhervorhebung
- Codeausschnitte
- IntelliSense für Cmdlets und vieles mehr
- Regel-basierte Analysen, die von bereitgestellte [PowerShell Script Analyzer](http://github.com/PowerShell/PSScriptAnalyzer)
- Gehe zu Definition von Cmdlets und Variablen
- Suchen von Verweisen von Cmdlets und Variablen
- Dokument und Arbeitsbereich-Symbol-Ermittlung
- Führen Sie die ausgewählten Auswahl von Code mithilfe von PowerShell <kbd>F8</kbd>
- Starten Sie die Onlinehilfe für das Symbol unter dem Cursor mit <kbd>STRG</kbd>+<kbd>F1</kbd>
- Grundlegende interaktive konsolenunterstützung!


## <a name="installing-the-extension"></a>Die Installation der Erweiterung

Sie können das offizielle Release des PowerShell-Erweiterung installieren, indem Sie die Schritte in der [Dokumentation zu Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/extensions).
Klicken Sie in den Bereich "Erweiterungen" Suchen Sie nach "PowerShell" Erweiterung, und installieren sie es.  Sie werden automatisch über alle Änderungen für die zukünftige Erweiterung benachrichtigt werden.

Sie können auch ein VSIX-Paket aus installieren unsere [Seite "Releases"](https://github.com/PowerShell/vscode-powershell/releases) und installieren Sie es über die Befehlszeile ausführen:

```powershell
azuredatastudio --install-extension PowerShell-<version>.vsix
```

## <a name="platform-support"></a>Plattformunterstützung

- **Windows 7 bis 10** mit Windows PowerShell Version 3 und höher, und PowerShell Core
- **Linux** mit PowerShell Core (alle PowerShell-unterstützten Distributionen)
- **MacOS** mit PowerShell Core

Lesen der [– häufig gestellte Fragen](https://github.com/PowerShell/vscode-powershell/wiki/FAQ) finden Sie Antworten auf häufig gestellte Fragen.

## <a name="installing-powershell-core"></a>Installieren von PowerShell Core

Wenn Sie Azure Data Studio unter MacOS oder Linux ausführen, müssen Sie auch PowerShell Core zu installieren.

PowerShell Core ist ein Open-Source-Projekt auf [GitHub](https://github.com/powershell/powershell).
Weitere Informationen zum Installieren von PowerShell Core unter MacOS oder Linux-Plattformen finden Sie unter den folgenden Artikeln:

- [Installieren von PowerShell Core unter Linux](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [Installieren von PowerShell Core unter macOS](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)

## <a name="example-scripts"></a>Beispielskripts

Es gibt einige Beispielskripts in der Erweiterungs `examples` Ordner, den Sie verwenden können, um PowerShell zum Bearbeiten und Debuggen Funktionen zu ermitteln.  Sehen Sie sich den enthaltenen ["Readme.MD"](https://github.com/PowerShell/vscode-powershell/blob/master/examples/README.md) Datei, um weitere Informationen zu deren Verwendung.

In diesem Ordner finden Sie unter folgendem Pfad:

```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.PowerShell-<version>/examples
```

oder wenn Sie die Preview-Version der Erweiterung verwenden

 ```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.powershell-preview-<version>/examples
```

Zum Öffnen/Beispiele für die der Erweiterung in Azure Data Studio anzeigen, führen Sie den folgenden Code aus der PowerShell-Eingabeaufforderung ein:

```powershell
azuredatastudio (Get-ChildItem $Home\.azuredatastudio\extensions\ms-vscode.PowerShell-*\examples)[-1]
```

### <a name="creating-and-opening-files"></a>Erstellen und Öffnen von Dateien

Verwenden Sie zum Erstellen und öffnen Sie eine neue Datei im Editor, und das New-EditorFile aus in das integrierte Terminal von PowerShell.

```powershell
PS C:\temp> New-EditorFile ExportData.ps1
```

Dieser Befehl kann für einen beliebigen Dateityp, nicht nur die PowerShell-Dateien.

```powershell
PS C:\temp> New-EditorFile ImportData.py
```

Um eine oder mehrere Dateien in Azure Data Studio zu öffnen, verwenden die `Open-EditorFile` Befehl.

```powershell
Open-EditorFile ExportData.ps1, ImportData.py
```

### <a name="no-focus-on-console-when-executing"></a>Ohne Fokus auf die Konsole beim Ausführen

Sie für diese Benutzer, die für die Arbeit mit SSMS vertraut sind, dann wissen, die Fähigkeit zum Ausführen einer Abfrage und dann wird es noch Mal erneut ausführen ohne wieder in den Abfragebereich zu wechseln.  In diesem Fall das Standardverhalten des Code-Editor merkwürdig erscheinen, Sie fühlen sich möglicherweise.  Zu den Fokus im Editor, beim Ausführen von mit <kbd>F8</kbd> ändern Sie die folgende Einstellung:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Der Standardwert ist `true` aus Gründen der Barrierefreiheit.

Beachten Sie diese Einstellung verhindert, dass den Fokus an der Konsole ändern, selbst wenn Sie einen Befehl, der explizit Aufrufe für die Eingabe, wie nutzen `Get-Credential`.

## <a name="sql-powershell-examples"></a>SQL PowerShell-Beispiele
Um diese Beispiele (siehe unten) zu verwenden, müssen Sie installieren das SqlServer-Modul aus der [PowerShell-Katalog](https://www.powershellgallery.com/packages/SqlServer).

```powershell
Install-Module -Name SqlServer
```

> [!NOTE]
> Mit Version `21.1.18102` und höher, die `SqlServer` -Modul unterstützt [PowerShell Core](https://github.com/PowerShell/PowerShell) 6.2 und, zusätzlich zu Windows PowerShell.

In diesem Beispiel verwenden wir die `Get-SqlInstance` Cmdlet zum Abrufen von Server-SMO-Objekte für ServerA und ServerB.  Die Standardausgabe für mit diesem Befehl den Instanznamen enthalten Version, Service Pack & CU-Update-Level-Instanzen.

```powershell
Get-SqlInstance -ServerInstance ServerA, ServerB
```

Hier ist ein Beispiel von möglichen Ausgabe:

```
Instance Name             Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------             -------    ------------ -----------  ------------ ----------------
ServerA                   13.0.5233  SP2          CU4          Windows      Windows Server 2016 Datacenter
ServerB                   14.0.3045  RTM          CU12         Linux        Ubuntu
```
Die `SqlServer` -Modul enthält einen Anbieter mit dem Namen `SQLRegistration` können Sie die folgenden Typen von gespeicherten SQL Server-Verbindungen programmgesteuert zugreifen:

+ Datenbank-Engine-Server (registrierten Server)
+ Zentrale Verwaltungsserver (CMS)
+ Analysis Services
+ Integration Services
+ Reporting Services

 Im folgenden Beispiel werden wir eine `dir` (alias für `Get-ChildItem`) zum Abrufen der Liste aller SQL Server-Instanzen, die in der Datei registrierte Server aufgeführt.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse 
```

Hier ist ein Beispiel von möglichen Ausgabe aussehen könnte:

```powershell
Mode Name
---- ----
-    ServerA
-    ServerB
-    localhost\SQL2017
-    localhost\SQL2016Happy
-    localhost\SQL2017
```

Für viele Vorgänge, bei denen eine Datenbank oder Objekte innerhalb einer Datenbank, die `Get-SqlDatabase` Cmdlet kann verwendet werden.  Wenn Sie Werte für das Angeben der `-ServerInstance` und `-Database` Parameter nur dieses eine Datenbank-Objekt abgerufen werden soll.  Aber wenn Sie nur angeben der `-ServerInstance` Parameter, eine vollständige Liste aller Datenbanken in dieser Instanz zurückgegeben.

Hier ist ein Beispiel von möglichen Ausgabe:

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

Im folgenden Beispiel verwendet die `Get-SqlDatabase` -Cmdlet zum Abrufen einer Liste aller Datenbanken auf der Serverinstanz ServerB präsentiert eine Tabellenraster (mithilfe der `Out-GridView` Cmdlet) auswählen, welche Datenbanken gesichert werden sollen.  Sobald der Benutzer auf die Schaltfläche "OK" klickt nur die markierten Datenbanken gesichert wird.

```powershell
Get-SqlDatabase -ServerInstance ServerB |
Out-GridView -PassThru |
Backup-SqlDatabase -CompressionOption On
```

In diesem Beispiel, in diesem Fall ruft die Liste aller SQL Server-Instanzen aufgeführt, die in der Datei registrierte Server ruft dann die `Get-SqlAgentJobHistory` welche Berichte alle fehlerhaften SQL-Agentenauftrags, seit Mitternacht für jede SQL Server-Instanz aufgeführt.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE {$_.Mode -ne 'd' } |
FOREACH {
    Get-SqlAgentJobHistory -ServerInstance  $_.Name -Since Midnight -OutcomesType Failed
}
```

In diesem Beispiel werden wir eine `dir` (alias für `Get-ChildItem`), rufen Sie die Liste aller SQL Server-Instanzen, die in der Datei registrierte Server aufgeführt, und verwenden Sie dann die `Get-SqlDatabase` -Cmdlet zum Abrufen einer Liste der Datenbanken für jede dieser Instanzen.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE { $_.Mode -ne 'd' } |
FOREACH {
    Get-SqlDatabase -ServerInstance $_.Name
}
```

Hier ist ein Beispiel von möglichen Ausgabe:

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

Wenn Sie Probleme mit der PowerShell-Erweiterung haben, finden Sie unter [Dokumentation zur Problembehandlung](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md) Informationen zur Diagnose und das Melden von Problemen.

#### <a name="security-note"></a>Sicherheitshinweis

Alle Sicherheitsprobleme zu erkennen, finden Sie unter [hier](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md#note-on-security).

## <a name="contributing-to-the-code"></a>Beitragen zum Code

Sehen Sie sich die [entwicklungsdokumentation](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) ausführliche Informationen zum mitwirken an diese Erweiterung!

## <a name="maintainers"></a>Verwalter

- [Keith Hill](https://github.com/rkeithhill) - [@r_keith_hill](http://twitter.com/r_keith_hill)
- [Tyler Leonhardt](https://github.com/tylerl0706) - [@TylerLeonhardt](http://twitter.com/tylerleonhardt)
- [Rob Holt](https://github.com/rjmholt)

## <a name="license"></a>License (Lizenz)

Diese Erweiterung ist [unter MIT-Lizenz lizenziert](https://github.com/PowerShell/vscode-powershell/blob/master/LICENSE.txt). Ausführliche Informationen zu den Binärdateien von Drittanbietern, die wir mit Versionen des Projekts enthalten, finden Sie unter den [drittanbieterhinweise](https://github.com/PowerShell/vscode-powershell/blob/master/Third%20Party%20Notices.txt) Datei.

## <a name="code-of-conductconduct-md"></a>[Verhaltenskodex][conduct-md]

Dieses Projekt folgt dem [Microsoft Open Source-Verhaltenskodex][conduct-code].
Weitere Informationen finden Sie unter den [Code von durchführen – häufig gestellte Fragen] [ conduct-FAQ] oder wenden Sie sich an [ opencode@microsoft.com ] [ conduct-email] weitere Fragen und Kommentare.

[conduct-code]: http://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: http://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
[conduct-md]: https://github.com/PowerShell/vscode-powershell/blob/master/CODE_OF_CONDUCT.md
