---
title: Neuerungen in SSMA für DB2 (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 06/11/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1cc38f85-3caa-42d0-8c76-a380c1d15c67
author: HJToland3
ms.author: Shamikg
ms.openlocfilehash: 036ae77a6d65ff396df60f54b38eeffba4e202f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086206"
---
# <a name="whats-new-in-ssma-for-db2-db2tosql"></a>Neuerungen in SSMA für DB2 (DB2ToSQL)

In diesem Artikel werden SQL Server Migration Assistant (SSMA) für die DB2-Änderungen in jeder Version aufgelistet.

## <a name="ssma-v82"></a>SSMA v8.2

Die v8.2-Version von SSMA für DB2 ist mit dem Probleme mit Verbindungen mit Azure SQL-Datenbank aus der SSMA-Konsolentool und die fehlenden COUNT_BIG-Spalte in der Deklaration von Sichten während der Konvertierung verbessert. Darüber hinaus enthält diese Version eine bestimmte Reihe von Fehlerbehebungen zur Verbesserung der Qualität und Konvertierung Metriken als auch Fehlerbehebungen für entwickelt:

* Ein Problem mit deaktivierten nicht gruppierten Indizes nach der Datenmigration.
* Erkennung von .NET Framework während der automatischen Installation.
* Eine vorübergehende Absturz, das auftritt, wenn eine neue Version heruntergeladen wird.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung möglicherweise den Fehler eines Updates aus SSMA v8. 1 auf v8.2. Wenn dieser Fehler auftritt, können herunterladen Sie die neue Version und installieren Sie ihn manuell klicken.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v81"></a>SSMA v8. 1

Die v8. 1-Version von SSMA für DB2 wird erweitert, um gezielte Fixes bereitzustellen, die entwickelt wurden, um die Qualität und Konvertierung von Metriken zu verbessern.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung möglicherweise den Fehler eines Updates von SSMA-Version 8.0 auf v8. 1. Wenn dieser Fehler auftritt, können herunterladen Sie die neue Version und installieren Sie ihn manuell klicken.

## <a name="ssma-v80"></a>SSMA v8. 0

Die Version 8.0 von SSMA für DB2 wird erweitert, um gezielte Fixes, die zur Verbesserung der Qualität und Konvertierung Metriken entwickelt bereitzustellen. Diese Version bietet auch die folgenden neuen Features:

* Unterstützung für **Azure verwaltete SQL-Datenbankinstanz** als Ziel. Sie können jetzt neue Projekte, die für verwaltete Azure SQL-Datenbankinstanz erstellen:

  ![SQL-DB MI-Projekt](../media/ssma-newproject-sqldbmi.png)

* Nach der Konvertierung **Fix Advisor**. Weitere Informationen finden sie [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbankschema-Auswahl.

  Bei der Verbindung mit der Quelle kann der Benutzer nun Datenbanken oder Schemas, die von Interesse auswählen. Wählen nur die Schemas, die Sie migrieren möchten, wird die sparen Sie Zeit, während der ersten Verbindung und SSMA-gesamtleistung verbessern.

  ![SSMA Filtern von Objekten](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

Die Version v7.10 von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Fixes soll, geben Sie zusätzliche Sicherheits- und Datenschutzfunktionen, um Änderungen in globalen Anforderungen zu erfüllen.
* Ein Fix für die Konvertierung von BEGIN / END-Blöcken.

## <a name="ssma-v79"></a>SSMA v7.9

Die Version v7.9 von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern.
* Unterstützt die in der SSMA-Befehlszeile, Data Type Mapping und Projekt-Einstellungen zu ändern.
* Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach der Konvertierung des Schemas ist es möglich, ein SSIS-Paket mit einer Option für das Kontextmenü zu erstellen.
* Die Azure SQL-Datenbank-Verbindungsdialogfeld in SSMA wurde auch geändert, um den vollqualifizierten Servernamen angeben. In früheren Versionen von SSMA musste das Präfix für die Azure SQL-Datenbank innerhalb von Projekten Einstellungen angegeben werden.

## <a name="ssma-v78"></a>SSMA V7. 8

Die V7. 8-Version von SSMA für DB2 enthält die folgenden Änderungen:

* Ändern Sie die Zuordnung eines Typs in den Projekteinstellungen hervorgehoben.
* Die Möglichkeit für Benutzer zum Deaktivieren der Telemetrie.

## <a name="ssma-v77"></a>SSMA v7.7

Die Version v7.7 von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern.
* Basierend auf der großen Nachfrage, ist die 32-Bit-Version von SSMA für DB2 zurück. Im Vergleich zu der vorherigen Implementierung (vor v7.4), es gibt zwei Installationspakete, aber sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version auf Grundlage der Konnektivitätskomponenten benötigen Sie auswählen. Es ist immer besser, nach Möglichkeit die 64-Bit-Version zu verwenden.

## <a name="ssma-v76"></a>SSMA v7.6

Die Version v7.6 von SSMA für DB2 wird erweitert, mit gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern und mit Unterstützung für SQL Server 2017 (öffentliche Vorschau). Unterstützung für SQL Server 2017 unter Windows und Linux wird in der öffentlichen Vorschau und darf nicht für Produktionsmigrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA V7. 5

Die Version 7.5 von SSMA für DB2 ist mit verschiedene Verbesserungen, um sicherzustellen, dass größere Barrierefreiheit für Personen mit behinderungen verbessert.

## <a name="ssma-v74"></a>SSMA v7.4

Die Version v7.4 von SSMA für DB2 enthält die folgenden Änderungen:

* Die **Abfragetimeout** Option ist während der Ermittlung an Quelle und Ziel am Schema jetzt verfügbar.

  ![Option Timeout für Remoteabfragen](../media/query-timeout_red.png)

* Die Qualität und Konvertierung-Metrik wurde durch gezielte Fixes, basierend auf Kundenfeedback verbessert.

  > [!IMPORTANT]
  > .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA-v7.4. Darüber hinaus v7.4 ab, die 32-Bit-Version von SSMA nicht mehr unterstützt.

## <a name="ssma-v73"></a>SSMA V7. 3

Die V7. 3-Version von SSMA für DB2 enthält die folgenden Änderungen:

* Verbesserte Qualität und Konvertierung Metrik mit gezielte Fixes, die basierend auf Kundenfeedback.
* SSMA-Erweiterungsframework verfügbar gemacht werden, über die folgenden Elemente:
  * Exportieren von Funktionen zu einem Projekt für die SQL Server Data Tools (SSDT).
    * Sie können jetzt Schemaskripts aus SSMA zu einem SSDT-Projekt exportieren. Die Schemaskripts können Sie zusätzliche schemaänderungen und Bereitstellen Ihrer Datenbank.

      ![Speichern Sie als SSDT-Projekt-Befehl](../media/export-schema-scripts_red.png)
  * Bibliotheken, die zum Ausführen von benutzerdefinierter Konvertierungen von SSMA genutzt werden können.
    * Sie können nun Code erstellen, die angepasste Syntax Konvertierungen und Konvertierungen, die zuvor vom SSMA verarbeitet wurden nicht verarbeiten kann.
      * Anweisungen dazu, einen benutzerdefinierten Konverter erstellen finden Sie in diesem Blogbeitrag [Erweitern von SQL Server Migration Assistant Konvertierungsfunktionen](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      * Ein Beispielprojekt für die Konvertierung aus dieser [Blogbeitrag](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>SSMA V7. 2

Die V7. 2-Version von SSMA für DB2 enthält die folgenden Änderungen:

* Verbesserte Qualität und Konvertierung Metrik mit gezielte Fixes, die basierend auf Kundenfeedback.
* Telemetrie Erweiterungen besser Datenpunkte zum Behandeln von Kundenproblemen und Verbessern SSMAs-Abschlussraten bereit.

## <a name="ssma-v71"></a>SSMA v7.1

Die Version v7.1 von SSMA für DB2 enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Dieses Feature ist in der technischen Vorschau und ermöglicht die Verlagerung von Schema und Daten an SQL-Zielserver.
* Unterstützung für automatische Updates für die neueste Version von SSMA herunterladen, sobald diese verfügbar ist.
* Installierbare SSMA-Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) übermittelt.

## <a name="may-2016"></a>Mai 2016

Die Version Mai 2016 von SSMA für DB2 enthält die folgenden Änderungen:  

* Unterstützung für SQL Server 2016 hinzugefügt.
* Hinzugefügte Konvertierung von DB2 in-Memory- und reguläre Tabellen in SQL Server-Funktionen für in-Memory- und Hekaton.
* Hinzugefügte Konvertierung von DB2-zugriffssteuerungen in SQL Server-Richtlinienobjekten (Sicherheit auf Zeilenebene für DB2).
* Hinzugefügte Konvertierung von DB2 die der systemversionsverwaltung unterliegende Tabellen in temporalen Tabellen mit SQL Server.
* Verbesserter DB2-Parser und Auflösung.
* Entfernt die Überprüfung der Installer für .net 2.0.
* Nicht benötigte *.dll entfernt aus Db2-Installer.
* Feste "Speichern" Projekt"und"Projekt öffnen"-Befehle für SSMA-Konsole.
* Feste "Securepassword"-Befehl für SSMA-Konsole.
* Korrektur von Objekten für das anfängliche laden zählen.
* Korrektur von Bug in den globalen Einstellungen.
  
## <a name="march-2016"></a>März 2016

Die vom März 2016 Preview-Version von SSMA für DB2 fügt Unterstützung für die Migration zu SQL Server 2016.

## <a name="january-2016"></a>Januar 2016

Die Version für den Wartungsmodus Januar 2016 von SSMA für DB2 enthält die folgenden Änderungen:  
  
* Unterstützung für eine Reihe von standard-Funktionen hinzugefügt.  
* DB2-Parser-Fehler behoben.  
* Feste DB2 v9 zOS erörtert Support (RFC 5690920).  
* Feste DB2 nicht aufgelöste Bezeichner Fehler während der Konvertierung auf.  
* Hinzugefügte Ansicht der Protokoll-Menüelement, SSMA (RFC 5706203).  
* Zusätzliche Telemetriedaten.
  
## <a name="november-2014"></a>November 2014

Die Version vom November 2014 von SSMA für DB2 war die erste Version.
