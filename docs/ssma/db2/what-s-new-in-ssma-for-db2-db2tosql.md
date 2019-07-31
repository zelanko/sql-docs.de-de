---
title: Neues in SSMA für DB2 (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 07/31/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1cc38f85-3caa-42d0-8c76-a380c1d15c67
author: HJToland3
ms.author: Shamikg
ms.openlocfilehash: 6c456334d9d77424c1955f392e8c8a5d16261234
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68632041"
---
# <a name="whats-new-in-ssma-for-db2-db2tosql"></a>Neues in SSMA für DB2 (DB2ToSQL)

In diesem Artikel wird SQL Server Migration Assistant (SSMA) für DB2-Änderungen in jeder Version aufgeführt.

## <a name="ssma-v83"></a>SSMA v 8.3

Das v 8.3-Release von SSMA für DB2 wurde durch gezielte Korrekturen verbessert, die zur Verbesserung der Qualität und der konvertierungsmetriken entwickelt wurden. Außerdem bietet diese Version von SSMA für DB2 Korrekturen, die Folgendes beinhaltet:

* Behandeln von Problemen mit Barrierefreiheit
* Grundlegende Unterstützung für den Typ "hierarchyid" in SQL Server hinzufügen
* Ersetzen der Verwendung der Trim-Funktion in z/OS-Ermittlungs Abfragen durch RTrim/LTrim
* Benutzern das Angeben der Paket Sammlung beim Herstellen einer Verbindung im "Standard Modus" erlauben (Standardwert ist "nullid")
* Konvertierung für CREATE TABLE als SELECT-Option hinzufügen
* Verbessern von Konvertierungen für globale temporäre Tabellen
* Beheben eines Problems mit der Eindeutigkeit von Objekt Eindeutigkeit zum Priorisieren von Tabellen gegenüber Einschränkungen, wenn Namen Konflikte haben
* Beheben eines Problems beim Laden von Standard Spaltenwerten für "Date" und "timestamp" für z/OS
* Unicode-Zeilenvorschub Zeichen (auch als nel bezeichnet) unterstützen
* Beheben eines Problems mit der Cursor Konvertierung mit fehlender Return to-Klausel
* Hinzufügen von Unterstützung für Bezeichnungen und GOTO

> [!IMPORTANT]
> Bei SSMA Version 7.4 und höheren Versionen ist .NET 4.5.2 eine erforderliche Installation.

## <a name="ssma-v82"></a>SSMA v 8.2

Die Version 8.2 von SSMA für DB2 wurde mit erweitert, um Probleme mit Verbindungen mit Azure SQL-Datenbank über das SSMA-Konsolen Tool und fehlende COUNT_BIG-Spalten in der views-Deklaration während der Konvertierung zu beheben. Darüber hinaus enthält diese Version einen Satz von Korrekturen, die für die Verbesserung von Qualitäts-und konvertierungsmetriken entworfen wurden, sowie Fehlerbehebungen für:

* Ein Problem mit deaktivierten nicht gruppierten Indizes nach der Datenmigration.
* Erkennung von .NET Framework während der automatischen Installation.
* Ein zeitweiliger Absturz, der auftritt, wenn eine neue Version heruntergeladen wird.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung kann zu einem Fehler bei einem Update von SSMA v 8.1 auf v 8.2 führen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter, und installieren Sie Sie manuell.

> [!IMPORTANT]
> Bei SSMA Version 7.4 und höheren Versionen ist .NET 4.5.2 eine erforderliche Installation.

## <a name="ssma-v81"></a>SSMA v 8.1

Die Version 8.1 von SSMA für DB2 wurde verbessert, um gezielte Korrekturen bereitzustellen, die zur Verbesserung der Qualität und der konvertierungsmetriken entwickelt wurden.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung kann zu einem Fehler bei einem Update von SSMA v 8.0 auf v 8.1 führen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter, und installieren Sie Sie manuell.

## <a name="ssma-v80"></a>SSMA v 8.0

Das v 8.0-Release von SSMA für DB2 wurde verbessert, um gezielte Korrekturen zur Verbesserung der Qualität und Konvertierungs Metriken bereitzustellen. Diese Version bietet auch die folgenden neuen Features:

* Unterstützung für **verwaltete Azure SQL-Datenbank-Instanz** als Ziel. Sie können jetzt neue Projekte erstellen, die auf verwaltete Azure SQL-Datenbank-Instanz abzielen:

  ![SQL-DB-Mi-Projekt](../media/ssma-newproject-sqldbmi.png)

* **Korrektur Ratgeber**nach der Konvertierung. Weitere Informationen hierzu [finden Sie hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbank/Schema-Auswahl.

  Beim Herstellen einer Verbindung mit der Quelle kann der Benutzer jetzt Datenbanken/Schemas von Interesse auswählen. Wenn Sie nur die Schemas auswählen, für die die Migration geplant ist, sparen Sie Zeit während der ersten Verbindung und verbessern die SSMA-Gesamtleistung.

  ![SSMA-Filter Objekte](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v 7.10

Das v 7.10-Release von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Korrekturen zur Bereitstellung zusätzlicher Sicherheits-und Datenschutz Maßnahmen zum erfüllen von Änderungen an globalen Anforderungen.
* Eine Korrektur für die Konvertierung von Begin-End-Blöcken.

## <a name="ssma-v79"></a>SSMA v 7.9

Die Version Version 7.9 von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Korrekturen, die Qualitäts-und konvertierungsmetriken verbessern.
* Unterstützung in der SSMA-Befehlszeile, um Datentyp Zuordnung und Projekteinstellungen zu ändern.
* Unterstützung für das Migrieren von Daten mithilfe von SQL Server Integration Services (SSIS). Nach dem Umrechnen des Schemas ist es möglich, ein SSIS-Paket zu erstellen, indem Sie mit der rechten Maustaste auf die Kontextmenü Option klicken.
* Das Azure SQL-Daten bankverbindungs Dialogfeld in SSMA wurde ebenfalls geändert, um den voll qualifizierten Servernamen anzugeben. In früheren Versionen von SSMA musste das Azure SQL-Daten Bank Präfix in den Projekteinstellungen explizit angegeben werden.

## <a name="ssma-v78"></a>SSMA v 7.8

Das Release v 7.8 von SSMA für DB2 enthält die folgenden Änderungen:

* Ändern Sie in den Projekteinstellungen hervorgehobene Typzuordnung.
* Die Möglichkeit für Benutzer, Telemetriedaten zu deaktivieren.

## <a name="ssma-v77"></a>SSMA v 7.7

Das Release v 7.7 von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Korrekturen, die Qualitäts-und konvertierungsmetriken verbessern.
* Basierend auf der beliebten Nachfrage ist die 32-Bit-Version von SSMA für DB2 zurück. Im Vergleich zur vorherigen Implementierung (vor v 7.4) gibt es zwei Installer-Pakete, aber Sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version basierend auf den Konnektivitätskomponenten auswählen, die Sie besitzen. Es ist immer ratsam, die 64-Bit-Version zu verwenden, wenn möglich.

## <a name="ssma-v76"></a>SSMA v 7.6

Die Version Version 7.6 von SSMA für DB2 wurde durch gezielte Korrekturen ergänzt, die Qualitäts-und konvertierungsmetriken sowie die Unterstützung für SQL Server 2017 (öffentliche Vorschau) verbessern. Unterstützung für SQL Server 2017 unter Windows und Linux befindet sich in der öffentlichen Vorschau Phase und sollte nicht für Produktions Migrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA v 7.5

Das Release v 7.5 von SSMA für DB2 wurde durch mehrere Verbesserungen verbessert, um mehr Barrierefreiheit für Menschen mit Behinderungen sicherzustellen.

## <a name="ssma-v74"></a>SSMA v 7.4

Die Version Version 7.4 von SSMA für DB2 enthält die folgenden Änderungen:

* Die Option **Abfrage Timeout** ist jetzt bei der Schema Objekt Ermittlung unter Quelle und Ziel verfügbar.

  ![Abfrage Timeout (Option)](../media/query-timeout_red.png)

* Die Qualitäts-und Konvertierungs Metrik wurde durch gezielte Korrekturen verbessert, basierend auf Kundenfeedback.

  > [!IMPORTANT]
  > .NET 4.5.2 ist eine Voraussetzung für die Installation von SSMA v 7.4. Ab Version 7.4 wird die 32-Bit-Version von SSMA nicht mehr unterstützt.

## <a name="ssma-v73"></a>SSMA v 7.3

Das Release v 7.3 von SSMA für DB2 enthält die folgenden Änderungen:

* Verbesserte Qualitäts-und Konvertierungs Metrik durch gezielte Korrekturen auf der Grundlage von Kundenfeedback.
* Das SSMA-Erweiterbarkeits Framework wurde über die folgenden Elemente verfügbar gemacht:
  * Exportieren Sie die-Funktionalität in ein SQL Server Data Tools-Projekt (SSDT).
    * Sie können jetzt Schema Skripts aus SSMA in ein SSDT-Projekt exportieren. Sie können die Schema Skripts verwenden, um zusätzliche Schema Änderungen vorzunehmen und die Datenbank bereitzustellen.

      ![Als SSDT-Projekt Befehl speichern](../media/export-schema-scripts_red.png)
  * Bibliotheken, die von SSMA zum Ausführen benutzerdefinierter Konvertierungen genutzt werden können.
    * Nun können Sie Code erstellen, mit dem benutzerdefinierte Syntax Konvertierungen und Konvertierungen verarbeitet werden können, die zuvor nicht von SSMA verarbeitet wurden.
      * Anweisungen zum Erstellen eines benutzerdefinierten Konverters finden Sie in diesem Blogbeitrag, in [dem die Konvertierungs Funktionen von SQL Server Migration Assistant erweitert](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)werden.
      * Herunterladen eines Beispielprojekts für die Konvertierung aus diesem [Blogbeitrag](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>SSMA v 7.2

Die Version Version 7.2 von SSMA für DB2 enthält die folgenden Änderungen:

* Verbesserte Qualitäts-und Konvertierungs Metrik durch gezielte Korrekturen auf der Grundlage von Kundenfeedback.
* Telemetrie-Verbesserungen, um bessere Datenpunkte zur Behandlung von Kundenproblemen und zur Verbesserung der Konvertierungsraten von SSMA bereitzustellen.

## <a name="ssma-v71"></a>SSMA v 7.1

Die Version Version 7.1 von SSMA für DB2 enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 wird jetzt als Zielplattform für die Migration unterstützt. Diese Funktion befindet sich in der Technical Preview und ermöglicht das Schema und die Daten Verschiebung für SQL Server-Zielserver.
* Unterstützung für automatische Updates, um die neueste Version von SSMA herunterzuladen, sobald Sie verfügbar ist.
* Installierbare SSMA-Binärdateien werden jetzt über Windows Installer-Paketdateien (MSI) übermittelt.

## <a name="may-2016"></a>Mai 2016

Die Version vom Mai 2016 von SSMA für DB2 enthält die folgenden Änderungen:  

* Unterstützung für SQL Server 2016 hinzugefügt.
* Die Konvertierung von DB2 in-Memory-und regulären Tabellen in SQL Server in-Memory-und hekaton-Features wurde hinzugefügt.
* Die Konvertierung von DB2-Zugriffs Steuerungen in SQL Server Richtlinien Objekte (Sicherheit auf Zeilenebene für DB2) wurde hinzugefügt.
* Die Konvertierung von DB2-Tabellen mit System Versionsverwaltung in SQL Server Temporale Tabellen wurde hinzugefügt.
* Verbesserter DB2-Parser und-Resolver.
* Die Installer-Überprüfung für .NET 2,0 wurde entfernt.
* Unnötige *. dll aus DB2-Installer entfernt.
* Die Befehle "Projekt speichern" und "Projekt öffnen" für die SSMA-Konsole wurden korrigiert.
* Der Befehl "SecurePassword" wurde für die SSMA-Konsole korrigiert.
* Das zählen von Objekten für das anfängliche laden wurde korrigiert.
* Fehler in globalen Einstellungen behoben.
  
## <a name="march-2016"></a>2016. März

Die Vorschauversion von SSMA für DB2 vom März 2016 bietet Unterstützung für die Migration zu SQL Server 2016.

## <a name="january-2016"></a>2016. Januar

Die Wartungsversion von SSMA für DB2 vom Januar 2016 enthält die folgenden Änderungen:  
  
* Unterstützung für eine Reihe von Standardfunktionen hinzugefügt.  
* Beheben von DB2-Parser-Fehlern.  
* Die Unterstützung für DB2 v9 zOS (RFC 5690920) wurde korrigiert.  
* Fehler bei aufgelösten DB2-Bezeichnern beim Konvertieren behoben.  
* Menü Element "View Log" zu SSMA hinzugefügt (RFC 5706203).  
* Telemetrie hinzugefügt.
  
## <a name="november-2014"></a>November 2014

Die Version vom November 2014 von SSMA für DB2 war die erste Version.
