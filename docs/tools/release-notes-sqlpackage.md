---
title: Versionshinweise zu DacFx und SqlPackage
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
ms.openlocfilehash: 0b034a0c0d449bd85afbfd46fa407e34921b8cf2
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82262127"
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
## <a name="185-sqlpackage"></a>18.5 sqlpackage

|Plattform|Download|Veröffentlichungsdatum|Version|Entwickeln
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2128142)|28. April 2020|18.5|15.0.4769.1|
|macOS .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2128145)|28. April 2020| 18.5|15.0.4769.1|
|Linux .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2128144)|28. April 2020| 18.5|15.0.4769.1|
|Windows .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2128143)|28. April 2020| 18.5|15.0.4769.1|

### <a name="features"></a>Features
| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Die Datenvertraulichkeitsklassifizierung wird jetzt für SQL Server 2008 und höher, Azure SQL-Datenbank und Azure SQL Data Warehouse unterstützt. |
| Bereitstellung | Unterstützung von Tabellenconstraints in Azure SQL Data Warehouse wurde hinzugefügt. |
| Bereitstellung | Unterstützung von sortiertem gruppiertem Columnstore-Index in Azure SQL Data Warehouse wurde hinzugefügt. |
| Bereitstellung | Unterstützung von externen Datenquellen (für Oracle, Teradata, MongoDB/CosmosDB, ODBC, Big Data-Cluster) und externen Tabellen für SQL Server 2019-Big Data-Cluster wurde hinzugefügt. |
| Bereitstellung | SQL Database Edge-Instanz wurde als unterstützte Edition hinzugefügt. |
| Bereitstellung | Unterstützung von Servernamen für verwaltete Instanzen im Format „\<Server>.\<DNS-Zone>.database.windows.net“ wurde hinzugefügt. |
| Bereitstellung | Unterstützung des Kopierbefehls in Azure SQL Data Warehouse wurde hinzufügt. |
| Bereitstellung | Die Bereitstellungsoption „IgnoreTablePartitionOptions“ für während der Veröffentlichung wurde hinzugefügt, um die Neuerstellung von Tabellen zu vermeiden, wenn die Partitionsfunktion für eine Tabelle für Azure SQL Data Warehouse geändert wird. |
| .NET Core | Unterstützung von Microsoft.Data.SqlClient in der .NET Core-Version von sqlpackage wurde hinzugefügt. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Fehlerbehebungen
| Fix | Details |
| :-- | :------ |
| Bereitstellung | Korrektur für die Veröffentlichung des DACPACs einer Datenbank, die einen externen Benutzer enthält, wodurch bisher folgender Fehler ausgelöst wurde: „Der Objektverweis ist nicht auf eine Instanz eines Objekts festgelegt.“ |
| Bereitstellung | Korrektur der Analyse eines JSON-Pfads als Ausdruck |
| Bereitstellung | Korrektur der Erstellung von GRANT-Anweisungen für die Berechtigungen AlterAnyDatabaseScopedConfiguration und AlterAnySensitivityClassification |
| Bereitstellung | Behebung eines Fehlers, aufgrund dessen die Berechtigung für externe Skripts nicht erkannt wurde |
| Bereitstellung | Korrektur für die Inline-Eigenschaft: Das implizite Hinzufügen der Eigenschaft sollte nicht als Unterschied angezeigt werden, aber die explizite Erwähnung sollte per Skript angezeigt werden. |
| Bereitstellung | Behebung eines Problems, bei dem Änderungen an einer Tabelle, auf die eine materialisierte Sicht verweist, dazu führen, dass ALTER VIEW-Anweisungen generiert werden, was in Azure SQL Data Warehouse für materialisierte Sichten nicht unterstützt wird |
| Bereitstellung | Behebung eines beim Veröffentlichen auftretenden Fehlers beim Hinzufügen einer Spalte zu einer Tabelle mit Daten für Azure SQL Data Warehouse |
| Bereitstellung | Behebung eines Fehlers in Bezug auf das Updateskript, das Daten in eine neue Tabelle verschieben sollte, wenn der Typ der Verteilungsspalte für Azure SQL Data Warehouse geändert wird (Datenverlustszenario) |
| ScriptDom | Behebung eines ScriptDom-Fehlers, bei dem keine nach einem Inlineindex definierten Inlineeinschränkungen erkannt werden konnten |
| ScriptDom | Ergänzung der fehlenden schließenden Klammer bei SYSTEM_TIME in ScriptDom in einer Batchanweisung |
| Always Encrypted | Behebung eines Fehlers, bei dem eine #tmpErrors-Tabelle nicht gelöscht wird, wenn sqlpackage die Verbindung erneut herstellt und die temporäre Tabelle bereits entfernt wurde, da diese entfernt wird, wenn die Verbindung getrennt wird |
| &nbsp; | &nbsp; |

## <a name="1841-sqlpackage"></a>18.4.1 sqlpackage

|Plattform|Download|Veröffentlichungsdatum|Version|Entwickeln
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2113703)|13. Dezember 2019|18.4.1|15.0.4630.1|
|macOS .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2113705)|13. Dezember 2019| 18.4.1|15.0.4630.1|
|Linux .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2113331)|13. Dezember 2019| 18.4.1|15.0.4630.1|
|Windows .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2113704)|13. Dezember 2019| 18.4.1|15.0.4630.1|

### <a name="fixes"></a>Fehlerbehebungen
| Fix | Details |
| :-- | :------ |
| ScriptDom |  In Version 18.3.1 wurde eine ScriptDom-Analyseregression eingeführt, bei der „RENAME“ fälschlicherweise als Token der obersten Ebene behandelt wurde, sodass die Analyse mit einem Fehler abgebrochen wurde.
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme 

| Funktion | Details |
| :------ | :------ |
| Bereitstellung |  In Version 18.4.1 wurde eine Regression eingeführt, welche den Fehler „Der Objektverweis ist nicht auf eine Instanz eines Objekts festgelegt.“ verursacht, wenn von einem extern angemeldeten Benutzer eine DACPAC-Datei bereitgestellt oder eine BACPAC-Datei importiert wird. Die Problemumgehung besteht in der Verwendung von sqlpackage 18.4. Zudem wird das Problem in der nächsten Version von sqlpackage behoben. | 
| &nbsp; | &nbsp; |

## <a name="184-sqlpackage"></a>18.4 sqlpackage

|Plattform|Download|Veröffentlichungsdatum|Version|Entwickeln
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2108813)|29. Oktober 2019|18.4|15.0.4573.2|
|macOS .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2108815)|29. Oktober 2019| 18.4|15.0.4573.2|
|Linux .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2108814)|29. Oktober 2019| 18.4|15.0.4573.2|
|Windows .NET Core |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2109019)|29. Oktober 2019| 18.4|15.0.4573.2|

### <a name="features"></a>Features

| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Unterstützung für die Bereitstellung in Azure SQL Data Warehouse (GA) hinzugefügt. | 
| Plattform | sqlpackage .NET Core GA für macOS, Linux und Windows. | 
| Sicherheit | SHA1-Codesignierung entfernt. |
| Bereitstellung | Unterstützung für neue Azure-Datenbankeditionen hinzugefügt: GeneralPurpose, BusinessCritical, Hyperscale |
| Bereitstellung | Unterstützung für verwaltete Instanzen bei AAD-Benutzern und -Gruppen hinzugefügt. |
| Bereitstellung | Unterstützung des /AccessToken-Parameters für sqlpackage in .NET Core hinzugefügt. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme 

| Funktion | Details |
| :------ | :------ |
| ScriptDom |  In Version 18.3.1 wurde eine ScriptDom-Analyseregression eingeführt, bei der „RENAME“ fälschlicherweise als Token der obersten Ebene behandelt wurde, sodass die Analyse mit einem Fehler abgebrochen wurde. Dies wird im nächsten sqlpackage-Release behoben. | 
| &nbsp; | &nbsp; |

### <a name="known-issues-for-net-core"></a>Bekannte Probleme bei .NET Core

| Funktion | Details |
| :------ | :------ |
| Importieren |  Bei BACPAC-Dateien mit komprimierten Dateien mit einer Größe von über 4 GB muss für den Import möglicherweise die .NET Core-Version von sqlpackage verwendet werden.  Dieses Verhalten ist darauf zurückzuführen, wie .NET Core ZIP-Header generiert. Diese sind zwar gültig, jedoch nicht von der vollständigen .NET Framework-Version von sqlpackage lesbar. | 
| Bereitstellung | Der Parameter /p:Storage=File wird nicht unterstützt. In .NET Core kann nur „Memory“ verwendet werden. | 
| Always Encrypted | sqlpackage .NET Core bietet keine Unterstützung für Always Encrypted-Spalten. | 
| Sicherheit | sqlpackage .NET Core bietet keine Unterstützung für den /ua-Parameter für die mehrstufige Authentifizierung. | 
| Bereitstellung | Ältere DACPAC- und BACPAC-Dateien der Version V2 mit Verwendung der JSON-Datenserialisierung werden nicht unterstützt. |
| &nbsp; | &nbsp; |

## <a name="1831-sqlpackage"></a>18.3.1 sqlpackage

|Plattform|Download|Veröffentlichungsdatum|Version|Entwickeln
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2102893)|13. September 2019|18.3.1|15.0.4538.1|
|macOS .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2102894)|13. September 2019| 18.3.1|15.0.4538.1|
|Linux .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2102978)|13. September 2019| 18.3.1|15.0.4538.1|
|Windows .NET Core (Vorschau)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2102979)|13. September 2019| 18.13.1|15.0.4538.1|

### <a name="features"></a>Features

| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Unterstützung für die Bereitstellung in Azure SQL Data Warehouse (Vorschau) hinzugefügt. | 
| Bereitstellung | Parameter „/p:DatabaseLockTimeout=(INT32 '60')“ zu sqlpackage hinzugefügt. | 
| Bereitstellung | Parameter „/p:LongRunningCommandTimeout=(INT32)“ zu sqlpackage hinzugefügt. |
| Exportieren/Extrahieren | Parameter „/p:TempDirectoryForTableData=(STRING)“ zu sqlpackage hinzugefügt. |
| Bereitstellung | Ermöglicht das Laden von Bereitstellungs-Contributors aus zusätzlichen Speicherorten. Bereitstellungs-Contributors werden aus demselben Verzeichnis geladen, in dem die DACPAC-Zieldatei bereitgestellt wird, sowie aus dem Verzeichnis „Erweiterungen“ relativ zur Binärdatei „sqlpackage.exe“. Außerdem wird der Parameter „/p:AdditionalDeploymentContributorPaths=(STRING)“ zu sqlpackage hinzugefügt, über den zusätzliche Verzeichnisse angegeben werden können. |
| Bereitstellung | Unterstützung für OPTIMIZE_FOR_SEQUENTIAL_KEY hinzugefügt. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Fehlerbehebungen

| Fix | Details |
| :-- | :------ |
| Bereitstellung | Korrektur, um automatische Indizes zu ignorieren, sodass diese bei der Bereitstellung nicht verworfen werden. | 
| Always Encrypted | Korrektur für die Behandlung von Always Encrypted-varchar-Spalten. | 
| Build/Bereitstellung | Korrektur zum Auflösen der nodes()-Methode für XML-Spaltensätze.| 
| ScriptDom | Korrektur für zusätzliche Szenarien, in denen die Zeichenfolge „URL“ als Token der obersten Ebene interpretiert wurde. | 
| Graph | Korrektur von generiertem TSQL-Code für Pseudospaltenverweise in Einschränkungen.  | 
| Exportieren | Generieren von zufälligen Kennwörtern, mit denen die Anforderungen im Hinblick auf die Komplexität erfüllt werden. | 
| Bereitstellung | Korrektur zum Berücksichtigen von Timeouts bei Befehlen, wenn Einschränkungen abgerufen werden. | 
| .NET Core (Vorschau) | Korrektur der Diagnoseprotokollierung für eine Datei. | 
| .NET Core (Vorschau) | Einsatz von Streaming für den Export von Tabellendaten, um große Tabellen zu unterstützen. | 
| &nbsp; | &nbsp; |

## <a name="182-sqlpackage"></a>18.2 sqlpackage

|Plattform|Download|Veröffentlichungsdatum|Version|Entwickeln
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2087429)|April 15, 2019|18.2|15.0.4384.2|
|macOS .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2087247)|April 15, 2019 | 18.2 |15.0.4384.2|
|Linux .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2087431)|April 15, 2019 | 18.2 |15.0.4384.2|

### <a name="features"></a>Features

| Funktion | Details |
| :------ | :------ |
| Graph | Unterstützung für Graphtabellen für Edgeeinschränkungen und Edgeeinschränkungsklauseln wurde hinzugefügt. |
| Bereitstellung | Aktivierung der Modellvalidierungsregel zur Unterstützung von 32 Spalten für Indexschlüssel für SQL Server 2016 und höher. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Fehlerbehebungen

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

### <a name="features"></a>Features

| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Es wurde Unterstützung für UTF-8-Sortierungen hinzugefügt. |
| Bereitstellung | Aktivierung von nicht gruppierten Columnstore-Indizes für eine indizierte Sicht. |
| Plattform | Umstellung auf .NET Core 2.2. | 
| Schemavergleich | Verwendung von arbeitsspeichergestütztem Speicher für den Schemavergleich in .NET Core. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Fehlerbehebungen

| Fix | Details |
| :-- | :------ |
| Leistung | Leistungskorrektur zur Verwendung der alten Kardinalitätsschätzung für Reverse Engineering-Abfragen. | 
| Leistung | Ein erhebliches Leistungsproblem beim Schemavergleich wurde behoben, das beim Generieren eines Skripts aufgetreten ist. | 
| Schemavergleich | Die Logik zur Erkennung von Schemaabweichungen wurde korrigiert, um bestimmte Sitzungen für erweiterte Ereignisse (extended event, xevent) zu ignorieren. |
| Graph | Die Importreihenfolge für Graphtabellen wurde korrigiert. | 
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

### <a name="features"></a>Features

| Funktion | Details |
| :------ | :------ |
| Bereitstellung | Es wurde Unterstützung für den Datenbank-Kompatibilitätsgrad 150 hinzugefügt. | 
| Bereitstellung | Es wurde Unterstützung für verwaltete Instanzen hinzugefügt. | 
| Leistung | Der Befehlszeilenparameter „MaxParallelism“ wurde hinzugefügt, um den Grad an Parallelität für Datenbankvorgänge angeben zu können. | 
| Sicherheit | Der Befehlszeilenparameter „AccessToken“ wurde hinzugefügt, um ein Authentifizierungstoken beim Herstellen einer Verbindung mit SQL Server angeben zu können. | 
| Importieren | Es wurde Unterstützung für das Streamen von BLOB-/CLOB-Datentypen für Importe hinzugefügt. | 
| Bereitstellung | Es wurde Unterstützung für die skalare UDF-Option „INLINE“ hinzugefügt. | 
| Graph | Es wurde Unterstützung für die Graphtabellensyntax „MERGE“ hinzugefügt. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Fehlerbehebungen

| Fix | Details |
| :-- | :------ |
| Graph | Korrigierte nicht aufgelöste Pseudospalte für Graphtabellen. |
| Bereitstellung | Es wurde ein Fehler behoben, der beim Erstellen einer Datenbank mit speicheroptimierten Dateigruppen auftrat, wenn speicheroptimierte Tabellen verwendet wurden. |
| Bereitstellung | Korrektur einschließlich der erweiterten Eigenschaften in externen Tabellen. |
| &nbsp; | &nbsp; |

## <a name="178-sqlpackage"></a>17.8 sqlpackage

Veröffentlichungsdatum: &nbsp; 22. Juni 2018  
Build: &nbsp; 14.0.4079.2

### <a name="features"></a>Features

| Funktion | Details |
| :------ | :------ |
| Diagnose | Verbesserte Fehlermeldungen für Verbindungsfehler, einschließlich der SqlClient-Ausnahmemeldung. |
| Bereitstellung | Unterstützung der Indexkomprimierung für einzelne Partitionsindizes beim Import/Export. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Fehlerbehebungen

| Fix | Details |
| :-- | :------ |
| Bereitstellung | Ein Reverse Engineering-Problem bei XML-Spaltensätzen in SQL 2017 und höher wurde behoben. | 
| Bereitstellung | Es wurde ein Problem behoben, bei dem die Skripterstellung für den Datenbank-Kompatibilitätsgrad 140 für Azure SQL-Datenbank ignoriert wurde. |
| &nbsp; | &nbsp; |

## <a name="1741-sqlpackage"></a>17.4.1 sqlpackage

Veröffentlichungsdatum: &nbsp; 25. Januar 2018  
Build: &nbsp; 14.0.3917.1

### <a name="features"></a>Features

| Funktion | Details |
| :------ | :------ |
| Importieren/Exportieren | Der Befehlszeilenparameter „ThreadMaxStackSize“ wurde hinzugefügt, um Transact-SQL mit einer großen Anzahl von geschachtelten Anweisungen analysieren zu können. |
| Bereitstellung | Unterstützung für die Datenbankkatalog-Sortierung. | 
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Fehlerbehebungen

| Fix | Details |
| :-- | :------ |
| Importieren | Es wurden Fehler behoben, die beim Importieren einer BACPAC-Datei von Azure SQL-Datenbank in eine lokale Instanz aufgrund der Meldung _Datenbank-Hauptschlüssel ohne Kennwort werden in dieser Version von SQL Server nicht unterstützt_ aufgetreten sind. |
| Graph | Es wurde ein Fehler bei nicht aufgelösten Pseudospalten für Graphtabellen behoben. |
| Schemavergleich | Korrektur der SQL-Authentifizierung für den Vergleich von Schemas. | 
| &nbsp; | &nbsp; |

## <a name="1740-sqlpackage"></a>17.4.0 sqlpackage

Veröffentlichungsdatum: &nbsp; 12. Dezember 2017  
Build: &nbsp; 14.0.3881.1

### <a name="features"></a>Features

| Funktion | Details |
| :------ | :------ |
| Bereitstellung |  Es wurde Unterstützung für die _temporale Aufbewahrungsrichtlinie_ für SQL 2017 (und höher) und Azure SQL-Datenbank hinzugefügt. | 
| Diagnose | Der Befehlszeilenparameter „/DiagnosticsFile:'C:\Temp\sqlpackage.log'“ wurde hinzugefügt, um einen Dateipfad zum Speichern von Diagnoseinformationen angeben zu können. | 
| Diagnose | Der Befehlszeilenparameter „/Diagnostics“ wurde hinzugefügt, um Diagnoseinformationen in der Konsole protokollieren zu können. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Fehlerbehebungen

| Fix | Details |
| :-- | :------ |
| Bereitstellung | Keine Blockierung beim Feststellen eines Datenbank-Kompatibilitätsgrads, der nicht verstanden wird. Stattdessen wird die neueste Version von Azure SQL-Datenbank oder die aktuelle lokale Plattform vorausgesetzt. |
| &nbsp; | &nbsp; |
