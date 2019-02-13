---
title: Microsoft DacFx & "Sqlpackage" Anmerkungen zu dieser Version | Microsoft-Dokumentation
description: Versionsanmerkungen zu Microsoft "Sqlpackage"
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: f9fe0558b169acea58bb98a4f9a07267549aa58f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013001"
---
# <a name="sqlpackage-release-notes"></a>Anmerkungen zur Version von "Sqlpackage"

**[Aktuelle Version herunterladen](sqlpackage-download.md)**

## <a name="sqlpackage-181"></a>sqlpackage 18.1

Releasedatum: 1. Februar 2019  
Build: 15.0.4316.1 

Die Version enthält die folgenden Features und Fixes:

- Unterstützung für die UTF8-Sortierungen.
- Behebung von Leistungsproblemen, die die legacy-kardinalitätsschätzung für reverse-engineering-Abfragen verwendet.
- Aktiviert die nicht gruppierten Columnstore-Indizes für eine indizierte Sichten.
- Eine erhebliche Schema vergleichen Leistungsproblem wurde behoben, wenn ein Skript zu generieren.
- Korrektur der Logik Schema Abweichung zur Erkennung, um bestimmte Xevent-Sitzungen zu ignorieren.
- Feste importieren, die Reihenfolge für die Graph-Tabellen.
- Korrektur, exportieren externe Tabellen mit Berechtigungen für Systemobjekte.
- In .NET Core 2.2 verschoben 
- Verwenden Sie Arbeitsspeicher-Speicherung für Schemavergleich in .NET Core.

Diese Version enthält, Cross-Platform Preview-Builds von "Sqlpackage", die .NET Core 2.2, und können unter MacOS und Linux ausgeführt wird. Diese Vorschauversion enthält die folgenden bekannten Probleme:

- Build- und bereitstellungs-Contributors werden nicht unterstützt.
- Ältere DACPAC- und bacpac-Dateien, die Serialisierung von JSON-Daten verwenden, werden nicht unterstützt.
- Auf die verwiesen wird .dacpacs (z. B. master.dacpac) kann aufgrund von Problemen mit der Groß-/Kleinschreibung Dateisysteme nicht aufgelöst werden.
  - Eine problemumgehung besteht darin, profitieren Sie den Namen der Verweisdatei (z. B. "MASTER". BACPAC-DATEI).
## <a name="sqlpackage-180"></a>sqlpackage 18.0

Releasedatum: 24. Oktober 2018  
Build: 15.0.4200.1 

Die Version enthält die folgenden Features und Fixes:

- Unterstützung für Datenbank-Kompatibilitätsgrad 150 hinzugefügt.
- Unterstützung für verwaltete Instanzen hinzugefügt.
- Hinzugefügte MaxParallelism Befehlszeilenparameter an den Grad an Parallelität für Datenbankvorgänge.
- Fügen Sie die AccessToken-Befehlszeilenparameter, um ein Authentifizierungstoken zu geben, wenn die Verbindung mit SQL Server hinzu.
- Die Unterstützung in Stream BLOB/CLOB-Datentypen für Importe.
- Unterstützung für skalare benutzerdefinierte Funktion 'INLINE'-Option.
- Unterstützung für Graph Table 'MERGE'-Syntax hinzugefügt.
- Feste nicht aufgelöste Pseudospalte für Graph-Tabellen.
- Korrektur, erstellen eine Datenbank mit optimierten Speicher-Datei, die Gruppen bei Tabellen speicheroptimierten verwendet werden.
- Es wurde behoben, einschließlich der erweiterten Eigenschaften in externen Tabellen.

## <a name="sqlpackage-178"></a>sqlpackage 17.8

Veröffentlichungsdatum: 22. Juni 2018  
Build: 14.0.4079.2  

Die Version enthält die folgenden Updates:

- Verbesserte Fehlermeldungen für Verbindungsfehler, einschließlich der SqlClient-Ausnahmemeldung an.
- Index-Komprimierung für Indizes, einzelne Partition für Import/Export unterstützt.
- Ein reverse engineering-Problem für XML-spaltensätze mit SQL 2017 und höher behoben.
- Ein Problem behoben, wurde der Datenbank-Kompatibilitätsgrad 140 scripting für Azure SQL-Datenbank ignoriert.

## <a name="sqlpackage-1741"></a>sqlpackage 17.4.1

Releasedatum: 25 Januar 2018  
Build: 14.0.3917.1

Die Version enthält die folgenden Updates:

- Wenn Sie eine Azure SQL-Datenbank-bacpac mit einer lokalen Instanz zu importieren, korrigiert Fehler aufgrund von "Datenbank-Hauptschlüssel ohne Kennwort nicht in dieser Version von SQL Server verwendet werden".
- Sortierungsunterstützung für Datenbank-Katalog.
- Wurde einen Fehler nicht aufgelöste Pseudo-Spalte, für die Graph-Tabellen.
- Hinzugefügte ThreadMaxStackSize Befehlszeilenparameter TSQL mit einer großen Anzahl von geschachtelten Anweisungen analysiert.
- Korrektur, verwenden die SchemaCompareDataModel mit SQL-Authentifizierung, zum Vergleichen von Schemas.

## <a name="sqlpackage-1740"></a>sqlpackage 17.4.0

Veröffentlichungsdatum: 12. Dezember 2017  
Build: 14.0.3881.1

Die Version enthält die folgenden Updates:

- Blockieren Sie nicht beim Auftreten von Datenbank-Kompatibilitätsgrad nicht verstanden. Stattdessen wird die neueste Azure SQL-Datenbank oder einer lokalen Plattform ausgegangen.
- Unterstützung für "temporale Aufbewahrungsrichtlinie" auf SQL 2017 +- und Azure SQL-Datenbank hinzugefügt.
- Hinzugefügt /DiagnosticsFile:"C:\Temp\sqlpackage.log" Befehlszeilenparameter verwenden, geben Sie einen Dateipfad zum Speichern der Diagnoseinformationen zu erhalten.
- Hinzugefügte/Diagnostics Befehlszeilenparameter an Diagnoseinformationen an der Konsole protokolliert.

