---
title: Versionshinweise zu DacFx und SqlPackage | Microsoft-Dokumentation
description: Versionshinweise zu Microsoft SqlPackage.
ms.custom: tools|sos
ms.date: 02/02/2019
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: 11e10f4a29b15efbd2b0ee513080a2000ae7e2f1
ms.sourcegitcommit: 82b70c39550402a2b0b327db32bf5ecf88b50d3c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73033048"
---
# <a name="release-notes-for-sqlpackageexe"></a>Versionshinweise zu „SqlPackage.exe“

**[Aktuelle Version herunterladen](sqlpackage-download.md)**

In diesem Artikel werden die in den veröffentlichten Versionen von „SqlPackage.exe“ bereitgestellten Features und Problembehebungen aufgelistet.

<!--
TODO:
The Introduction text needs to add clarity regarding the relationship between
'SqlPackage.exe' and 'DacFx' (the Microsoft 'Data-Tier Application Framework').
One added sentence would be sufficient.

Or, if there is no relationship, remove 'DacFx' from the metadata 'title:'.

I discussed this with SStein (SteveStein).
Thanks.  GeneMi (MightyPen in GitHub).  2019-03-27
-->

## <a name="184-sqlpackage"></a>18.4 sqlpackage

|Platform|Herunterladen|Veröffentlichungsdatum|Versionsoptionen|Erstellen
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2108813)|29. Oktober 2019|18.4|15.0.4573.2|
|macOS .net Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2108815)|29. Oktober 2019| 18.4|15.0.4573.2|
|Linux .net Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2108814)|29. Oktober 2019| 18.4|15.0.4573.2|
|Windows .net Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2109019)|29. Oktober 2019| 18.4|15.0.4573.2|

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Hinzufügen von Unterstützung für die Bereitstellung in Azure SQL Data Warehouse (GA). | 
| Platform | Sqlpackage .net Core GA für macOS, Linux und Windows. | 
| Security | Entfernen der SHA1-Code Signatur. |
| Bereitstellung | Unterstützung für neue Azure-Daten Bank Editionen hinzufügen: General Purpose, BusinessCritical, Hyperscale |
| Bereitstellung | Fügen Sie verwaltete Instanz Unterstützung für Aad-Benutzer und-Gruppen hinzu. |
| Bereitstellung | Unterstützung des/AccessToken-Parameters für Sqlpackage in .net Core. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme 

| Funktion | Details |
| :------ | :------ |
| ScriptDom |  Eine ScriptDom-paramenungs Regression wurde in 18.3.1 eingeführt, wobei "Rename" fälschlicherweise als Token der obersten Ebene behandelt wird, sodass die Verarbeitung fehlschlägt. Dies wird in der nächsten Version von Sqlpackage korrigiert. | 
| &nbsp; | &nbsp; |

### <a name="known-issues-for-net-core"></a>Bekannte Probleme bei .net Core

| Funktion | Details |
| :------ | :------ |
| Importieren |  Für BacPac-Dateien mit komprimierten Dateien mit einer Größe von mehr als 4 GB müssen Sie möglicherweise die .net Core-Version von Sqlpackage verwenden, um den Import auszuführen.  Dieses Verhalten ist darauf zurückzuführen, wie .net Core ZIP-Header generiert, die zwar gültig sind, aber nicht von der .net Full Framework-Version von Sqlpackage lesbar sind. | 
| Bereitstellung | Der/p: Storage = File-Parameter wird nicht unterstützt. In .net Core wird nur der Arbeitsspeicher unterstützt. | 
| Always Encrypted | Sqlpackage .net Core unterstützt keine Always Encrypted Spalten. | 
| Security | Sqlpackage .net Core unterstützt den/UA-Parameter für Multi-Factor Authentication nicht. | 
| Bereitstellung | Ältere DACPAC- und BACPAC-Dateien der Version V2 mit Verwendung der JSON-Datenserialisierung werden nicht unterstützt. |
| &nbsp; | &nbsp; |

## <a name="1831-sqlpackage"></a>18.3.1 sqlpackage

|Platform|Herunterladen|Veröffentlichungsdatum|Versionsoptionen|Erstellen
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2102893)|13. September 2019|18.3.1|15.0.4538.1|
|macOS .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2102894)|13. September 2019| 18.3.1|15.0.4538.1|
|Linux .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2102978)|13. September 2019| 18.3.1|15.0.4538.1|
|Windows .net Core (Vorschau)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2102979)|13. September 2019| 18.13.1|15.0.4538.1|

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Unterstützung für die Bereitstellung in Azure SQL Data Warehouse (Vorschau) hinzufügen. | 
| Bereitstellung | Fügen Sie Sqlpackage den Parameter/p: databaselocktimeout = (Int32 "60") hinzu. | 
| Bereitstellung | Fügen Sie Sqlpackage den Parameter/p: longrunningcommandtimeout = (Int32) hinzu. |
| Exportieren/extrahieren | Fügen Sie Sqlpackage den/p: tempdirectoryfortabledata = (String)-Parameter hinzu. |
| Bereitstellung | Ermöglicht, dass Bereitstellungs Mitwirkende aus zusätzlichen Speicherorten geladen werden. Die Mitwirkenden der Bereitstellung werden aus demselben Verzeichnis geladen wie das Ziel. dacpac wird bereitgestellt, das Erweiterungs Verzeichnis relativ zur Binärdatei Sqlpackage. exe und der/p: additionaldeploymentcontributorpath = (String)-Parameter, der Sqlpackage hinzugefügt wird. Gibt an, wo zusätzliche Verzeichnis Speicherorte angegeben werden können. |
| Bereitstellung | Unterstützung für OPTIMIZE_FOR_SEQUENTIAL_KEY hinzufügen. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Bereitstellung | Korrektur, um automatische Indizes zu ignorieren, sodass Sie bei der Bereitstellung nicht gelöscht werden. | 
| Always Encrypted | Korrektur für die Behandlung von Always Encrypted varchar-Spalten. | 
| Build/Bereitstellung | Korrektur zum Auflösen der Nodes ()-Methode für XML-Spalten Sätze.| 
| ScriptDom | Korrigieren Sie weitere Fälle, in denen die URL-Zeichenfolge als Token der obersten Ebene interpretiert wurde. | 
| Diagramm | Korrektur von generiertem TSQL für Pseudo Spalten Verweise in Einschränkungen.  | 
| Exportieren | Generieren Sie zufällige Kenn Wörter, die Komplexitäts Anforderungen entsprechen. | 
| Bereitstellung | Korrektur zum berücksichtigen von Befehls Timeouts beim Abrufen von Einschränkungen. | 
| .NET Core (Vorschau) | Korrektur der Diagnoseprotokollierung in einer Datei. | 
| .NET Core (Vorschau) | Verwenden Sie Streaming zum Exportieren von Tabellendaten, um große Tabellen zu unterstützen. | 
| &nbsp; | &nbsp; |

## <a name="182-sqlpackage"></a>18.2 sqlpackage

|Platform|Herunterladen|Veröffentlichungsdatum|Versionsoptionen|Erstellen
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2087429)|April 15, 2019|18.2|15.0.4384.2|
|macOS .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2087247)|April 15, 2019 | 18.2 |15.0.4384.2|
|Linux .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2087431)|April 15, 2019 | 18.2 |15.0.4384.2|

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Diagramm | Unterstützung für Graphtabellen für Edgeeinschränkungen und Edgeeinschränkungsklauseln wurde hinzugefügt. |
| Bereitstellung | Aktivierung der Modellvalidierungsregel zur Unterstützung von 32 Spalten für Indexschlüssel für SQL Server 2016 und höher. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Bereitstellung | Korrektur des Reverse Engineering einer SQL Server 2016 RTM-Datenbank aufgrund eines nicht unterstützten Abfragehinweises. |
| Bereitstellung | Korrektur der Bereitstellungsreihenfolge von AUTOCLOSE ALTER-Anweisungen, die vor der Erstellung von FILEGROUP-Anweisungen auftreten. |
| ScriptDom | Korrektur der ScriptDom-Analyseregression, bei der die Zeichenfolge „URL“ als Token der obersten Ebene interpretiert wurde. |
| Bereitstellung | Korrektur einer Nullverweisausnahme beim Analysieren einer ALTER TABLE ADD INDEX-Anweisung. | 
| Schemavergleich | Korrigierter Schemavergleich für persistierte berechnete Spalten, die NULL-Werte zulassen und immer als unterschiedlich angezeigt werden.|
| &nbsp; | &nbsp; |

## <a name="181-sqlpackage"></a>18.1 sqlpackage

Veröffentlichungsdatum: &nbsp; 1. Februar 2019  
Build: &nbsp; 15.0.4316.1  
Vorschauversion.

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Es wurde Unterstützung für UTF-8-Sortierungen hinzugefügt. |
| Bereitstellung | Aktivierung von nicht gruppierten Columnstore-Indizes für eine indizierte Sicht. |
| Platform | Umstellung auf .NET Core 2.2. | 
| Schemavergleich | Verwendung von arbeitsspeichergestütztem Speicher für den Schemavergleich in .NET Core. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Leistung | Leistungskorrektur zur Verwendung der alten Kardinalitätsschätzung für Reverse Engineering-Abfragen. | 
| Leistung | Ein erhebliches Leistungsproblem beim Schemavergleich wurde behoben, das beim Generieren eines Skripts aufgetreten ist. | 
| Schemavergleich | Die Logik zur Erkennung von Schemaabweichungen wurde korrigiert, um bestimmte Sitzungen für erweiterte Ereignisse (extended event, xevent) zu ignorieren. |
| Diagramm | Die Importreihenfolge für Graphtabellen wurde korrigiert. | 
| Exportieren | Der Export von externen Tabellen mit Objektberechtigungen wurde korrigiert. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme

Diese Version enthält plattformübergreifende Vorabversionen von SqlPackage, die auf .NET Core 2.2 abzielen. SqlPackage kann unter macOS und Linux ausgeführt werden.

| Bekanntes Problem | Details |
| :---------- | :------ |
| Bereitstellung | Für .NET Core werden Build- und Bereitstellungs-Contributors nicht unterstützt. | 
| Bereitstellung | Ältere DACPAC- und BACPAC-Dateien mit Verwendung der JSON-Datenserialisierung werden für .NET Core nicht unterstützt. | 
| Bereitstellung | Referenzierte DACPAC-Dateien (z. B. „master.dacpac“) können aufgrund von Problemen mit Dateisystemen mit Groß-/Kleinschreibung für .NET Core möglicherweise nicht aufgelöst werden. | Eine Problemumgehung besteht darin, den Namen der Verweisdatei groß zu schreiben (Beispiel: „MASTER.BACPAC“). |
| &nbsp; | &nbsp; |

## <a name="180-sqlpackage"></a>18.0 sqlpackage

Veröffentlichungsdatum: &nbsp; 24. Oktober 2018  
Build: &nbsp; 15.0.4200.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Es wurde Unterstützung für den Datenbank-Kompatibilitätsgrad 150 hinzugefügt. | 
| Bereitstellung | Es wurde Unterstützung für verwaltete Instanzen hinzugefügt. | 
| Leistung | Der Befehlszeilenparameter „MaxParallelism“ wurde hinzugefügt, um den Grad an Parallelität für Datenbankvorgänge angeben zu können. | 
| Security | Der Befehlszeilenparameter „AccessToken“ wurde hinzugefügt, um ein Authentifizierungstoken beim Herstellen einer Verbindung mit SQL Server angeben zu können. | 
| Importieren | Es wurde Unterstützung für das Streamen von BLOB-/CLOB-Datentypen für Importe hinzugefügt. | 
| Bereitstellung | Es wurde Unterstützung für die skalare UDF-Option „INLINE“ hinzugefügt. | 
| Diagramm | Es wurde Unterstützung für die Graphtabellensyntax „MERGE“ hinzugefügt. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Diagramm | Korrigierte nicht aufgelöste Pseudospalte für Graphtabellen. |
| Bereitstellung | Es wurde ein Fehler behoben, der beim Erstellen einer Datenbank mit speicheroptimierten Dateigruppen auftrat, wenn speicheroptimierte Tabellen verwendet wurden. |
| Bereitstellung | Korrektur einschließlich der erweiterten Eigenschaften in externen Tabellen. |
| &nbsp; | &nbsp; |

## <a name="178-sqlpackage"></a>17.8 sqlpackage

Veröffentlichungsdatum: &nbsp; 22. Juni 2018  
Build: &nbsp; 14.0.4079.2

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Diagnose | Verbesserte Fehlermeldungen für Verbindungsfehler, einschließlich der SqlClient-Ausnahmemeldung. |
| Bereitstellung | Unterstützung der Indexkomprimierung für einzelne Partitionsindizes beim Import/Export. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Bereitstellung | Ein Reverse Engineering-Problem bei XML-Spaltensätzen in SQL 2017 und höher wurde behoben. | 
| Bereitstellung | Es wurde ein Problem behoben, bei dem die Skripterstellung für den Datenbank-Kompatibilitätsgrad 140 für Azure SQL-Datenbank ignoriert wurde. |
| &nbsp; | &nbsp; |

## <a name="1741-sqlpackage"></a>17.4.1 sqlpackage

Veröffentlichungsdatum: &nbsp; 25. Januar 2018  
Build: &nbsp; 14.0.3917.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Importieren/Exportieren | Der Befehlszeilenparameter „ThreadMaxStackSize“ wurde hinzugefügt, um Transact-SQL mit einer großen Anzahl von geschachtelten Anweisungen analysieren zu können. |
| Bereitstellung | Unterstützung für die Datenbankkatalog-Sortierung. | 
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Importieren | Es wurden Fehler behoben, die beim Importieren einer BACPAC-Datei von Azure SQL-Datenbank in eine lokale Instanz aufgrund der Meldung _Datenbank-Hauptschlüssel ohne Kennwort werden in dieser Version von SQL Server nicht unterstützt_ aufgetreten sind. |
| Diagramm | Es wurde ein Fehler bei nicht aufgelösten Pseudospalten für Graphtabellen behoben. |
| Schemavergleich | Die SQL-Authentifizierung zum Vergleichen von Schemas wurde korrigiert. | 
| &nbsp; | &nbsp; |

## <a name="1740-sqlpackage"></a>17.4.0 sqlpackage

Veröffentlichungsdatum: &nbsp; 12. Dezember 2017  
Build: &nbsp; 14.0.3881.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Bereitstellung |  Es wurde Unterstützung für die _temporale Aufbewahrungsrichtlinie_ für SQL 2017 (und höher) und Azure SQL-Datenbank hinzugefügt. | 
| Diagnose | Der Befehlszeilenparameter „/DiagnosticsFile:'C:\Temp\sqlpackage.log'“ wurde hinzugefügt, um einen Dateipfad zum Speichern von Diagnoseinformationen angeben zu können. | 
| Diagnose | Der Befehlszeilenparameter „/Diagnostics“ wurde hinzugefügt, um Diagnoseinformationen in der Konsole protokollieren zu können. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Bereitstellung | Keine Blockierung beim Feststellen eines Datenbank-Kompatibilitätsgrads, der nicht verstanden wird. Stattdessen wird die neueste Version von Azure SQL-Datenbank oder die aktuelle lokale Plattform vorausgesetzt. |
| &nbsp; | &nbsp; |
