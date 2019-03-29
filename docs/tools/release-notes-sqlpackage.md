---
title: DacFx und "Sqlpackage" Anmerkungen zu dieser Version | Microsoft-Dokumentation
description: Versionshinweise für Microsoft "Sqlpackage".
ms.custom: tools|sos
ms.date: 02/02/2019
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: de45add2b02686f990d68f7c1c23eec385848751
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538776"
---
# <a name="release-notes-for-sqlpackageexe"></a>Anmerkungen zu dieser Version für SqlPackage.exe

**[Aktuelle Version herunterladen](sqlpackage-download.md)**

Dieser Artikel listet die Features und Fixes, die von der veröffentlichten Versionen von SqlPackage.exe bereitgestellt werden.

<!--
TODO:
The Introduction text needs to add clarity regarding the relationship between
'SqlPackage.exe' and 'DacFx' (the Microsoft 'Data-Tier Application Framework').
One added sentence would be sufficient.

Or, if there is no relationship, remove 'DacFx' from the metadata 'title:'.

I discussed this with SStein (SteveStein).
Thanks.  GeneMi (MightyPen in GitHub).  2019-03-27
-->

## <a name="181-sqlpackage"></a>18.1 sqlpackage

Veröffentlichungsdatum: &nbsp; 1. Februar 2019  
Build: &nbsp; 15.0.4316.1  
Preview-Version.

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Unterstützung für die UTF8-Sortierungen. | &nbsp; |
| Aktiviert die nicht gruppierten Columnstore-Indizes für eine indizierte Sicht. | &nbsp; |
| In .NET Core 2.2 verschoben. | &nbsp; |
| Verwenden Sie Arbeitsspeicher-Speicherung für Schemavergleich in .NET Core. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Behebung von Leistungsproblemen, die die legacy-kardinalitätsschätzung für reverse-engineering-Abfragen verwendet. | &nbsp; |
| Eine erhebliche Schema vergleichen Leistungsproblem wurde behoben, wenn ein Skript zu generieren. | &nbsp; |
| Korrektur der Logik Schema Abweichung zur Erkennung, um bestimmte Sitzungen für erweiterte Ereignisse (Xevent) zu ignorieren. | &nbsp; |
| Feste importieren, die Reihenfolge für die Graph-Tabellen. | &nbsp; |
| Korrektur, exportieren externe Tabellen mit Berechtigungen für Systemobjekte. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme

Diese Version enthält Cross-Platform Preview-Builds von "Sqlpackage", die auf .NET Core 2.2 abzielen. Die "Sqlpackage" kann unter MacOS und Linux ausführen.

| Bekanntes Problem | Details |
| :---------- | :------ |
| Build- und bereitstellungs-Contributors werden nicht unterstützt. | &nbsp; |
| Ältere DACPAC- und bacpac-Dateien, die Serialisierung von JSON-Daten verwenden, werden nicht unterstützt. | &nbsp; |
| Auf die verwiesen wird .dacpacs (z. B. master.dacpac) kann aufgrund von Problemen mit der Groß-/Kleinschreibung Dateisysteme nicht aufgelöst werden. | Eine problemumgehung besteht darin, profitieren Sie den Namen der Verweisdatei (z. B. "MASTER". BACPAC-DATEI). |
| &nbsp; | &nbsp; |

## <a name="180-sqlpackage"></a>18.0 sqlpackage

Veröffentlichungsdatum: &nbsp; 24. Oktober 2018  
Build: &nbsp; 15.0.4200.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Unterstützung für Datenbank-Kompatibilitätsgrad 150 hinzugefügt. | &nbsp; |
| Unterstützung für verwaltete Instanzen hinzugefügt. | &nbsp; |
| Hinzugefügte MaxParallelism Befehlszeilenparameter an den Grad an Parallelität für Datenbankvorgänge. | &nbsp; |
| Hinzugefügte AccessToken Befehlszeilen Parameter ein Authentifizierungstoken an, beim Verbinden mit SQL Server. | &nbsp; |
| Die Unterstützung in Stream BLOB/CLOB-Datentypen für Importe. | &nbsp; |
| Unterstützung für skalare benutzerdefinierte Funktion 'INLINE'-Option. | &nbsp; |
| Unterstützung für Graph Table 'MERGE'-Syntax hinzugefügt. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Feste nicht aufgelöste Pseudospalte für Graph-Tabellen. | &nbsp; |
| Korrektur, erstellen eine Datenbank mit optimierten Speicher-Datei, die Gruppen bei Tabellen speicheroptimierten verwendet werden. | &nbsp; |
| Es wurde behoben, einschließlich der erweiterten Eigenschaften in externen Tabellen. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="178-sqlpackage"></a>17.8 sqlpackage

Veröffentlichungsdatum: &nbsp; 22. Juni 2018  
Build: &nbsp; 14.0.4079.2

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Verbesserte Fehlermeldungen für Verbindungsfehler, einschließlich der SqlClient-Ausnahmemeldung an. | &nbsp; |
| Index-Komprimierung für Indizes, einzelne Partition für Import/Export unterstützt. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Ein reverse engineering-Problem für XML-spaltensätze mit SQL 2017 und höher behoben. | &nbsp; |
| Ein Problem behoben, wurde der Datenbank-Kompatibilitätsgrad 140 scripting für Azure SQL-Datenbank ignoriert. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1741-sqlpackage"></a>17.4.1 sqlpackage

Veröffentlichungsdatum: &nbsp; 25 Januar 2018  
Build: &nbsp; 14.0.3917.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Hinzugefügte ThreadMaxStackSize Befehlszeilenparameter zum Analysieren von Transact-SQL mit einer großen Anzahl von geschachtelten Anweisungen. | &nbsp; |
| Sortierungsunterstützung für Datenbank-Katalog. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Wenn Sie eine Azure SQL-Datenbank-bacpac mit einer lokalen Instanz zu importieren, korrigiert Fehler aufgrund von _Datenbank-Hauptschlüssel ohne Kennwort werden nicht in dieser Version von SQL Server unterstützt_. | &nbsp; |
| Wurde einen Fehler nicht aufgelöste Pseudo-Spalte, für die Graph-Tabellen. | &nbsp; |
| Korrektur, verwenden die SchemaCompareDataModel mit SQL-Authentifizierung, zum Vergleichen von Schemas. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1740-sqlpackage"></a>17.4.0 sqlpackage

Veröffentlichungsdatum: &nbsp; 12. Dezember 2017  
Build: &nbsp; 14.0.3881.1

### <a name="features"></a>Funktionen

| Funktion | Details |
| :------ | :------ |
| Unterstützung für _temporale Aufbewahrungsrichtlinie_ SQL 2017 und höher und Azure SQL-Datenbank. | &nbsp; |
| Hinzugefügt /DiagnosticsFile:"C:\Temp\sqlpackage.log" Befehlszeilenparameter verwenden, geben Sie einen Dateipfad zum Speichern der Diagnoseinformationen zu erhalten. | &nbsp; |
| Hinzugefügte/Diagnostics Befehlszeilenparameter an Diagnoseinformationen an der Konsole protokolliert. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Problembehebungen

| Fix | Details |
| :-- | :------ |
| Wenn eine Datenbank-Kompatibilitätsgrad festgestellt wird, der nicht verstanden wird, werden nicht blockiert werden. | Stattdessen wird die neueste Version Azure SQL-Datenbank oder eine lokale Plattform ausgegangen. |
| &nbsp; | &nbsp; |
