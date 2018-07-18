---
title: Microsoft DacFx & "Sqlpackage" Anmerkungen zu dieser Version | Microsoft-Dokumentation
description: Versionsanmerkungen zu Microsoft "Sqlpackage"
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sqlpackage
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: 7d05ec161b89e548cf529bc82c6d714a1960fb0f
ms.sourcegitcommit: 0dff9dd43e80eee900eb92d25df9ca18397f3485
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37080151"
---
# <a name="sqlpackage-release-notes"></a>Anmerkungen zur Version von "Sqlpackage"

**[Aktuelle Version herunterladen](sqlpackage-download.md)**

## <a name="sqlpackage-178"></a>sqlpackage 17.8

Veröffentlichungsdatum: 22. Juni 2018  
Build: 14.0.4079.2  

Die Version enthält die folgenden Updates:

- Verbesserte Fehlermeldungen für Verbindungsfehler, einschließlich der SqlClient-Ausnahmemeldung an.
- Hinzugefügte MaxParallelism Befehlszeilenparameter an den Grad an Parallelität für Datenbankvorgänge.
- Index-Komprimierung für Indizes, einzelne Partition für Import/Export unterstützt.
- Ein reverse engineering-Problem für XML-spaltensätze mit SQL 2017 und höher behoben.
- Ein Problem behoben, wurde der Datenbank-Kompatibilitätsgrad 140 scripting für Azure SQL-Datenbank ignoriert.

## <a name="sqlpackage-1741"></a>sqlpackage 17.4.1

Veröffentlichungsdatum: 25 Januar 2018  
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

## <a name="sqlpackage-on-macos-and-linux-001-preview"></a>"Sqlpackage" unter MacOS und Linux 0.0.1 (Vorschau)

Veröffentlichungsdatum: 9. Mai 2018  
Build: 15.0.4057.1

Diese Version enthält die Cross-Platform Preview-Builds von "Sqlpackage", die auf .NET Core 2.0 abzielt, und kann unter MacOS und Linux ausführen. 

Diese Version ist eine frühe Vorschau mit folgenden bekannten Probleme:

- Der /p:CommandTimeout-Parameter ist schwer auf jeweils 120 codiert.
- Build- und bereitstellungs-Contributors werden nicht unterstützt.
  - Wird nach dem Wechsel zu .NET Core 2.1, in denen System.ComponentModel.Composition.dll unterstützt behoben werden.
  - Groß-/Kleinschreibung Pfade behandeln müssen.
- SQL CLR-benutzerdefinierte Typen werden nicht unterstützt, einschließlich SQL Server-CLR-UDT-Typen: "sqlgeography", "sqlgeometry" und SqlHierarchyId.
- Ältere DACPAC- und bacpac-Dateien, die Serialisierung von JSON-Daten verwenden, werden nicht unterstützt.
- Auf die verwiesen wird .dacpacs (z. B. master.dacpac) kann aufgrund von Problemen mit der Groß-/Kleinschreibung Dateisysteme nicht aufgelöst werden.
  - Eine problemumgehung besteht darin, profitieren Sie den Namen der Verweisdatei (z. B. "MASTER". BACPAC-DATEI).