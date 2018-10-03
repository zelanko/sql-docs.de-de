---
title: Neuerungen in SSMA für DB2 (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 09/22/2018
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1cc38f85-3caa-42d0-8c76-a380c1d15c67
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: deaaaf4141c363606abfc86720ba4ed043426af6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723808"
---
# <a name="whats-new-in-ssma-for-db2-db2tosql"></a>Neuerungen in SSMA für DB2 (DB2ToSQL)
In diesem Artikel werden die SSMA für DB2-Änderungen in jeder Version aufgelistet.  

## <a name="ssma-v710"></a>SSMA v7.10
Die Version v7.10 von SSMA für DB2 enthält die folgenden Änderungen:
- Gezielte Fixes soll, geben Sie zusätzliche Sicherheits- und Datenschutzfunktionen, um Änderungen in globalen Anforderungen zu erfüllen.
- Ein Fix für die Konvertierung von BEGIN / END-Blöcken.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v79"></a>SSMA v7.9
Die Version v7.9 von SSMA für DB2 enthält die folgenden Änderungen:
- Gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern.
- Unterstützt die in der SSMA-Befehlszeile, Data Type Mapping und Projekt-Einstellungen zu ändern.
- Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach der Konvertierung des Schemas ist es möglich, ein SSIS-Paket mit einer Option für das Kontextmenü zu erstellen.
- Die Azure SQL-Datenbank-Verbindungsdialogfeld in SSMA wurde auch geändert, um den vollqualifizierten Servernamen angeben. In früheren Versionen von SSMA musste das Präfix für die Azure SQL-Datenbank innerhalb von Projekten Einstellungen angegeben werden.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v78"></a>SSMA V7. 8
Die V7. 8-Version von SSMA für DB2 enthält die folgenden Änderungen:
- Hervorgehobene Änderung Typzuordnung in den Projekteinstellungen.
- Die Möglichkeit für Benutzer zum Deaktivieren der Telemetrie wird bereitgestellt.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v77"></a>SSMA v7.7
Die Version v7.7 von SSMA für DB2 enthält die folgenden Änderungen:
- SSMA für DB2 wurde gezielte Fixes erweitert, die die Qualität und Konvertierung von Metriken zu verbessern.
- Basierend auf der großen Nachfrage, ist die 32-Bit-Version von SSMA für DB2 zurück. Im Vergleich zu der vorherigen Implementierung (vor v7.4), es gibt zwei Installationspakete, aber sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version auf Grundlage der Konnektivitätskomponenten benötigen Sie auswählen. Es ist immer besser, nach Möglichkeit die 64-Bit-Version zu verwenden.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v76"></a>SSMA v7.6
Die Version v7.6 von SSMA für DB2 wurde verbessert, gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern und mit Unterstützung für SQL Server 2017 (öffentliche Vorschau). Unterstützung für SQL Server 2017 unter Windows und Linux wird in der öffentlichen Vorschau und darf nicht für Produktionsmigrationen verwendet werden.

> [!IMPORTANT]
> SSMA v7.4 und höher .net 4.5.2 ist eine Voraussetzung für Installation, und die 32-Bit-Version des Tools wurde eingestellt.

## <a name="ssma-v75"></a>SSMA V7. 5
Die Version 7.5 von SSMA für DB2 wurde verbessert, mit einer Reihe von Verbesserungen an größere Barrierefreiheit für Personen mit behinderungen sicherzustellen.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA V7. 5. Darüber hinaus wird v7.4 ab, die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v74"></a>SSMA v7.4
Die Version v7.4 von SSMA für DB2 enthält die folgenden Änderungen:
- Die **Abfragetimeout** Option ist während der Ermittlung an Quelle und Ziel am Schema jetzt verfügbar.
![Option Timeout für Remoteabfragen](../media/query-timeout_red.png)

- Die Qualität und Konvertierung-Metrik wurde durch gezielte Fixes, basierend auf Kundenfeedback verbessert.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA-v7.4. Darüber hinaus wird v7.4 ab, die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v73"></a>SSMA V7. 3
Die V7. 3-Version von SSMA für DB2 enthält die folgenden Änderungen:
- Verbesserte Qualität und Konvertierung Metrik mit gezielte Fixes, die basierend auf Kundenfeedback.
- SSMA-Erweiterungsframework verfügbar gemacht werden, über die folgenden Elemente:
  - Exportieren von Funktionen zu einem Projekt für die SQL Server Data Tools (SSDT).
    -   Sie können jetzt Schemaskripts aus SSMA zu einem SSDT-Projekt exportieren. Die Schemaskripts können Sie zusätzliche schemaänderungen und Bereitstellen Ihrer Datenbank.
![Speichern Sie als SSDT-Projekt-Befehl](../media/export-schema-scripts_red.png)
  - Bibliotheken, die zum Ausführen von benutzerdefinierter Konvertierungen von SSMA genutzt werden können.
    - Sie können nun Code erstellen, die angepasste Syntax Konvertierungen und Konvertierungen, die zuvor vom SSMA verarbeitet wurden nicht verarbeiten kann.
      - Anweisungen dazu, einen benutzerdefinierten Konverter erstellen finden Sie in diesem Blogbeitrag [Erweitern von SQL Server Migration Assistant Konvertierungsfunktionen](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Ein Beispielprojekt für die Konvertierung aus dieser [Blogbeitrag](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>SSMA V7. 2
Die V7. 2-Version von SSMA für DB2 enthält die folgenden Änderungen:
- Verbesserte Qualität und Konvertierung Metrik mit gezielte Fixes, die basierend auf Kundenfeedback.
- Telemetrie Erweiterungen besser Datenpunkte zum Behandeln von Kundenproblemen und Verbessern SSMAs-Abschlussraten bereit.

## <a name="ssma-v71"></a>SSMA v7.1
Die v7.1-Version von SSMA für Access umfasst die folgenden Änderungen:
- SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Dieses Feature ist in der technischen Vorschau und ermöglicht die Verlagerung von Schema und Daten an SQL-Zielserver.
- SSMA unterstützt jetzt die automatische Updates für die neueste Version von SSMA herunterladen, sobald diese verfügbar ist.
- Installierbare SSMA-Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) übermittelt.

**Ressourcen**

[Erweitern von SQL Server Migration Assistant Funktionen](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Bewerten und Migrieren von Daten aus nicht-Microsoft-datenplattformen mit SQL Server *(mit der Oracle-Beispiel)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Mai 2016  
Die Version Mai 2016 von SSMA für DB2 enthält die folgenden Änderungen:  

-  Unterstützung für SQL Server 2016 hinzugefügt.
-  Hinzugefügte Konvertierung von DB2 in-Memory- und reguläre Tabellen in SQL Server-Funktionen für in-Memory- und Hekaton.
-  Hinzugefügte Konvertierung von DB2-zugriffssteuerungen in SQL Server-Richtlinienobjekten (Sicherheit auf Zeilenebene für DB2).
-  Hinzugefügte Konvertierung von DB2 die der systemversionsverwaltung unterliegende Tabellen in temporalen Tabellen mit SQL Server.
-  Verbesserter DB2-Parser und Auflösung.
-  Entfernt die Überprüfung der Installer für .net 2.0.
-  Nicht benötigte *.dll entfernt aus Db2-Installer.
-  Feste "Speichern" Projekt"und"Projekt öffnen"-Befehle für SSMA-Konsole.
-  Feste "Securepassword"-Befehl für SSMA-Konsole.
-  Korrektur von Objekten für das anfängliche laden zählen.
-  Korrektur von Bug in den globalen Einstellungen.
  
## <a name="march-2016"></a>März 2016  
Die vom März 2016 Preview-Version von SSMA für DB2 enthält die folgenden Änderungen:  
  
-  Unterstützung für die Migration zu SQL Server 2016.  
  
## <a name="january-2016"></a>Januar 2016  
Die Version für den Wartungsmodus Januar 2016 von SSMA für DB2 enthält die folgenden Änderungen:  
  
-  Unterstützung für eine Reihe von standard-Funktionen hinzugefügt.  
-  DB2-Parser-Fehler behoben.  
-  Feste DB2 v9 zOS erörtert Support (RFC 5690920).  
-  Feste DB2 nicht aufgelöste Bezeichner Fehler während der Konvertierung auf.  
-  Hinzugefügte Ansicht der Protokoll-Menüelement, SSMA (RFC 5706203).  
-  Zusätzliche Telemetriedaten.
  
## <a name="november-2014"></a>November 2014  
Die Version vom November 2014 von SSMA für DB2 war die erste Version.
