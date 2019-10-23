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
ms.openlocfilehash: ad2f4eaadfb2140facc5bebd8d1f70cf163d1380
ms.sourcegitcommit: 6413b7495313830ad1ae5aefe0c09e8e7a284b07
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2019
ms.locfileid: "71016879"
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
| Azure SQL Data Warehouse (Vorschau) | Fügen Sie Unterstützung für die Bereitstellung in Azure SQL Data Warehouse hinzu. | 
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
| .Net Core (Vorschau) | Korrektur der Diagnoseprotokollierung in einer Datei. | 
| .Net Core (Vorschau) | Verwenden Sie Streaming zum Exportieren von Tabellendaten, um große Tabellen zu unterstützen. | 
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
| Unterstützung für Graphtabellen für Edgeeinschränkungen und Edgeeinschränkungsklauseln wurde hinzugefügt. | &nbsp; |
| Aktivierung der Modellvalidierungsregel zur Unterstützung von 32 Spalten für Indexschlüssel für SQL Server 2016 und höher. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Korrektur des Reverse Engineering einer SQL Server 2016 RTM-Datenbank aufgrund eines nicht unterstützten Abfragehinweises. | &nbsp; |
| Korrektur der Bereitstellungsreihenfolge von AUTOCLOSE ALTER-Anweisungen, die vor der Erstellung von FILEGROUP-Anweisungen auftreten. | &nbsp; |
| Korrektur der ScriptDom-Analyseregression, bei der die Zeichenfolge „URL“ als Token der obersten Ebene interpretiert wurde. | &nbsp; |
| Korrektur einer Nullverweisausnahme beim Analysieren einer ALTER TABLE ADD INDEX-Anweisung. | &nbsp; |
| Korrigierter Schemavergleich für persistierte berechnete Spalten, die NULL-Werte zulassen und immer als unterschiedlich angezeigt werden.| &nbsp; |
| &nbsp; | &nbsp; |

## <a name="181-sqlpackage"></a>18.1 sqlpackage

Veröffentlichungsdatum: &nbsp; 1. Februar 2019  
Build: &nbsp; 15.0.4316.1  
Vorschauversion.

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Es wurde Unterstützung für UTF-8-Sortierungen hinzugefügt. | &nbsp; |
| Aktivierung von nicht gruppierten Columnstore-Indizes für eine indizierte Sicht. | &nbsp; |
| Umstellung auf .NET Core 2.2. | &nbsp; |
| Verwendung von arbeitsspeichergestütztem Speicher für den Schemavergleich in .NET Core. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Leistungskorrektur zur Verwendung der alten Kardinalitätsschätzung für Reverse Engineering-Abfragen. | &nbsp; |
| Ein erhebliches Leistungsproblem beim Schemavergleich wurde behoben, das beim Generieren eines Skripts aufgetreten ist. | &nbsp; |
| Die Logik zur Erkennung von Schemaabweichungen wurde korrigiert, um bestimmte Sitzungen für erweiterte Ereignisse (extended event, xevent) zu ignorieren. | &nbsp; |
| Die Importreihenfolge für Graphtabellen wurde korrigiert. | &nbsp; |
| Der Export von externen Tabellen mit Objektberechtigungen wurde korrigiert. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme

Diese Version enthält plattformübergreifende Vorabversionen von SqlPackage, die auf .NET Core 2.2 abzielen. SqlPackage kann unter macOS und Linux ausgeführt werden.

| Bekanntes Problem | Details |
| :---------- | :------ |
| Build- und Bereitstellungs-Contributors werden nicht unterstützt. | &nbsp; |
| Ältere DACPAC- und BACPAC-Dateien, die die JSON-Datenserialisierung verwenden, werden nicht unterstützt. | &nbsp; |
| Referenzierte DACPAC-Dateien (z. B. „master.dacpac“) können aufgrund von Problemen mit Dateisystemen mit Groß-/Kleinschreibung möglicherweise nicht aufgelöst werden. | Eine Problemumgehung besteht darin, den Namen der Verweisdatei groß zu schreiben (Beispiel: „MASTER.BACPAC“). |
| &nbsp; | &nbsp; |

## <a name="180-sqlpackage"></a>18.0 sqlpackage

Veröffentlichungsdatum: &nbsp; 24. Oktober 2018  
Build: &nbsp; 15.0.4200.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Es wurde Unterstützung für den Datenbank-Kompatibilitätsgrad 150 hinzugefügt. | &nbsp; |
| Es wurde Unterstützung für verwaltete Instanzen hinzugefügt. | &nbsp; |
| Der Befehlszeilenparameter „MaxParallelism“ wurde hinzugefügt, um den Grad an Parallelität für Datenbankvorgänge angeben zu können. | &nbsp; |
| Der Befehlszeilenparameter „AccessToken“ wurde hinzugefügt, um ein Authentifizierungstoken beim Herstellen einer Verbindung mit SQL Server angeben zu können. | &nbsp; |
| Es wurde Unterstützung für das Streamen von BLOB-/CLOB-Datentypen für Importe hinzugefügt. | &nbsp; |
| Es wurde Unterstützung für die skalare UDF-Option „INLINE“ hinzugefügt. | &nbsp; |
| Es wurde Unterstützung für die Graphtabellensyntax „MERGE“ hinzugefügt. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Korrigierte nicht aufgelöste Pseudospalte für Graphtabellen. | &nbsp; |
| Es wurde ein Fehler behoben, der beim Erstellen einer Datenbank mit speicheroptimierten Dateigruppen auftrat, wenn speicheroptimierte Tabellen verwendet wurden. | &nbsp; |
| Korrektur einschließlich der erweiterten Eigenschaften in externen Tabellen. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="178-sqlpackage"></a>17.8 sqlpackage

Veröffentlichungsdatum: &nbsp; 22. Juni 2018  
Build: &nbsp; 14.0.4079.2

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Verbesserte Fehlermeldungen für Verbindungsfehler, einschließlich der SqlClient-Ausnahmemeldung. | &nbsp; |
| Unterstützung der Indexkomprimierung für einzelne Partitionsindizes beim Import/Export. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Ein Reverse Engineering-Problem bei XML-Spaltensätzen in SQL 2017 und höher wurde behoben. | &nbsp; |
| Es wurde ein Problem behoben, bei dem die Skripterstellung für den Datenbank-Kompatibilitätsgrad 140 für Azure SQL-Datenbank ignoriert wurde. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1741-sqlpackage"></a>17.4.1 sqlpackage

Veröffentlichungsdatum: &nbsp; 25. Januar 2018  
Build: &nbsp; 14.0.3917.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Der Befehlszeilenparameter „ThreadMaxStackSize“ wurde hinzugefügt, um Transact-SQL mit einer großen Anzahl von geschachtelten Anweisungen analysieren zu können. | &nbsp; |
| Unterstützung für die Datenbankkatalog-Sortierung. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Es wurden Fehler behoben, die beim Importieren einer BACPAC-Datei von Azure SQL-Datenbank in eine lokale Instanz aufgrund der Meldung _Datenbank-Hauptschlüssel ohne Kennwort werden in dieser Version von SQL Server nicht unterstützt_ aufgetreten sind. | &nbsp; |
| Es wurde ein Fehler bei nicht aufgelösten Pseudospalten für Graphtabellen behoben. | &nbsp; |
| Korrektur der Verwendung von SchemaCompareDataModel mit SQL-Authentifizierung zum Vergleichen von Schemas. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1740-sqlpackage"></a>17.4.0 sqlpackage

Veröffentlichungsdatum: &nbsp; 12. Dezember 2017  
Build: &nbsp; 14.0.3881.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Es wurde Unterstützung für die _temporale Aufbewahrungsrichtlinie_ für SQL 2017 (und höher) und Azure SQL-Datenbank hinzugefügt. | &nbsp; |
| Der Befehlszeilenparameter „/DiagnosticsFile:'C:\Temp\sqlpackage.log'“ wurde hinzugefügt, um einen Dateipfad zum Speichern von Diagnoseinformationen angeben zu können. | &nbsp; |
| Der Befehlszeilenparameter „/Diagnostics“ wurde hinzugefügt, um Diagnoseinformationen in der Konsole protokollieren zu können. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Keine Blockierung beim Feststellen eines Datenbank-Kompatibilitätsgrads, der nicht verstanden wird. | Stattdessen wird die neueste Version von Azure SQL-Datenbank oder die aktuelle lokale Plattform vorausgesetzt. |
| &nbsp; | &nbsp; |
