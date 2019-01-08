---
title: Neuerungen in SSMA für SAP ASE (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/22/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 460506c8c29a3ee92f362db57719a711626d83a0
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52398313"
---
# <a name="whats-new-in-ssma-for-sap-ase-sybasetosql"></a>Neuerungen in SSMA für SAP ASE (SybaseToSQL)
In diesem Artikel werden die SSMA für SAP ASE (früher SSMA für Sybase) Änderungen in jeder Version aufgelistet. 

## <a name="ssma-v710"></a>SSMA v7.10
Die Version v7.10 von SSMA für SAP ASE wurde verbessert, gezielte Fixes soll, geben Sie zusätzliche Sicherheits- und Datenschutzfunktionen, um Änderungen in globalen Anforderungen zu erfüllen.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v79"></a>SSMA v7.9
Die Version v7.9 von SSMA für SAP ASE enthält die folgenden Änderungen:
- Gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern.
- Unterstützt die in der SSMA-Befehlszeile, Data Type Mapping und Projekt-Einstellungen zu ändern.
- Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach der Konvertierung des Schemas ist es möglich, ein SSIS-Paket mit einer Option für das Kontextmenü zu erstellen.
- Die Azure SQL-Datenbank-Verbindungsdialogfeld in SSMA wurde auch geändert, um den vollqualifizierten Servernamen angeben. In früheren Versionen von SSMA musste das Präfix für die Azure SQL-Datenbank innerhalb von Projekten Einstellungen angegeben werden.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v78"></a>SSMA V7. 8
Die V7. 8-Version von SSMA für SAP ASE enthält die folgenden Änderungen:
- Hervorgehobene Änderung Typzuordnung in den Projekteinstellungen.
- Die Möglichkeit für Benutzer zum Deaktivieren der Telemetrie wird bereitgestellt.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v77"></a>SSMA v7.7
Die Version v7.7 von SSMA für SAP ASE enthält die folgenden Änderungen:
- SSMA für SAP ASE wurde gezielte Fixes erweitert, die die Qualität und Konvertierung von Metriken zu verbessern.
- Basierend auf der großen Nachfrage, ist die 32-Bit-Version von SSMA für SAP ASE zurück. Im Vergleich zu der vorherigen Implementierung (vor v7.4), es gibt zwei Installationspakete, aber sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version auf Grundlage der Konnektivitätskomponenten benötigen Sie auswählen. Es ist immer besser, nach Möglichkeit die 64-Bit-Version zu verwenden.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v76"></a>SSMA v7.6
Die Version v7.6 von SSMA für SAP ASE enthält die folgenden Änderungen:
- SSMA für SAP ASE wurde verbessert, gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern und mit Unterstützung für SQL Server 2017 (öffentliche Vorschau). Unterstützung für SQL Server 2017 unter Windows und Linux wird in der öffentlichen Vorschau und darf nicht für Produktionsmigrationen verwendet werden.
- SSMA für SAP ASE wurde aktualisiert, um für die Konvertierung von Sybase-Funktionen zu unterstützen.

> [!IMPORTANT]
> SSMA v7.4 und höher .net 4.5.2 ist eine Voraussetzung für Installation, und die 32-Bit-Version des Tools wurde eingestellt.

## <a name="ssma-v75"></a>SSMA V7. 5
Die Version 7.5 von SSMA für SAP ASE enthält die folgenden Änderungen:
-   Durch zahlreiche Verbesserungen, um sicherzustellen, dass größere Barrierefreiheit für Personen mit behinderungen verbessert.
-   Aktualisiert, um das Erstellen oder zu ersetzen die Syntax unterstützen.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA V7. 5. Darüber hinaus wird v7.4 ab, die 32-Bit-Version von SSMA eingestellt.  

## <a name="ssma-v74"></a>SSMA v7.4
Die Version v7.4 von SSMA für Sybase enthält die folgenden Änderungen:
- Die **Abfragetimeout** Option ist während der Ermittlung an Quelle und Ziel am Schema jetzt verfügbar.
![Option Timeout für Remoteabfragen](../media/query-timeout_red.png)
- Die Qualität und Konvertierung-Metrik wurde durch gezielte Fixes, basierend auf Kundenfeedback verbessert.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA-v7.4. Darüber hinaus wird v7.4 ab, die 32-Bit-Version von SSMA eingestellt.  

## <a name="ssma-v73"></a>SSMA V7. 3
Die V7. 3-Version von SSMA für Sybase enthält die folgenden Änderungen:
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
Die V7. 2-Version von SSMA für Sybase enthält die folgenden Änderungen:
- Verbesserte Qualität und Konvertierung Metrik mit gezielte Fixes, die basierend auf Kundenfeedback.
- Telemetrie Erweiterungen besser Datenpunkte zum Behandeln von Kundenproblemen und Verbessern SSMAs-Abschlussraten bereit.

## <a name="ssma-v71"></a>SSMA v7.1
Die v7.1-Version von SSMA für Access umfasst die folgenden Änderungen:
- SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Dieses Feature ist in der technischen Vorschau und unterstützt das Verschieben von Schema und Daten an SQL-Zielserver.
- SSMA unterstützt jetzt die automatische Updates für die neueste Version von SSMA herunterladen, sobald diese verfügbar ist.
- Installierbare SSMA-Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) übermittelt.

**Ressourcen**

[Erweitern von SQL Server Migration Assistant Funktionen](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Bewerten und Migrieren von Daten aus nicht-Microsoft-datenplattformen mit SQL Server *(mit der Oracle-Beispiel)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Mai 2016  
Die Version Mai 2016 von SSMA für Sybase enthält die folgenden Änderungen:  

-  Unterstützung für SQL Server 2016 hinzugefügt.
-  Entfernt die Überprüfung der Installer für .net 2.0.
-  Aktualisierte Erweiterungspaket Abhängigkeit von .net 3.5 zu .net 4.0.
-  Feste "Speichern" Projekt"und"Projekt öffnen"-Befehle für SSMA-Konsole.
-  Feste "Securepassword"-Befehl für SSMA-Konsole.
-  Korrektur von Objekten für das anfängliche laden zählen.
-  Korrektur von Bug in den globalen Einstellungen.

## <a name="march-2016"></a>März 2016  
Die vom März 2016 Preview-Version von SSMA für Sybase enthält die folgenden Änderungen:  
  
-  Unterstützung für die Migration zu SQL Server 2016.  
  
## <a name="january-2016"></a>Januar 2016  
Die Version für den Wartungsmodus Januar 2016 von SSMA für Sybase enthält die folgenden Änderungen:  
  
-  Hinzugefügte Ansicht der Protokoll-Menüelement, SSMA (RFC 5706203).  
-  Zusätzliche Telemetriedaten. 
  
## <a name="july-2014"></a>Juli 2014  
Die Version von Juli 2014 von SSMA für Sybase enthält die folgenden Änderungen:  
  
-  Verbesserte codekonvertierung für Azure SQL-Datenbank.  
-  Extension-Pack-Funktion zum Schema zur Unterstützung von Azure SQL-Datenbank verschoben.  
-  Zusätzliche leistungsverbesserungen, die für Datenbanken mit mehr als 10 KB Objekten getestet.  
-  Zusätzliche Verbesserungen der Benutzeroberfläche für den Umgang mit großen Anzahl von Objekten.  
-  Die Möglichkeit zum Markieren von "bekannte" LOB-Schemas (sodass sie bei der Konvertierung ignoriert werden können) hinzugefügt.  
-  Geschwindigkeit der Konvertierung wird hinzugefügt.  
-  Die Möglichkeit, Objekte in der Benutzeroberfläche angezeigt wird hinzugefügt. 
-  Reduzierte Berichtsgröße von mehr als 25 %.  
-  Verbesserte Fehlermeldungen für nicht verarbeitete Konstrukte.  
  
## <a name="april-2014"></a>April 2014  
Die Version April 2014 von SSMA für Sybase enthält die folgenden Änderungen:  
  
-   Die Unterstützung von MS SQL Server 2014.  
-   Behobenen Problemen in Bezug auf die Konvertierung in Azure.  
-   Behobenen Problemen in Bezug auf unsichtbare Berichtsseiten in Internet Explorer 10.  
  
## <a name="january-2012"></a>Januar 2012  
Die Januar 2012-Version von SSMA für Sybase enthält die folgenden Änderungen:  
  
-   Unterstützung für die Konvertierung der Rollback-Trigger.  
-   Bereitgestellte Lösung für die Konvertierung von@ROWCOUNT und @@ERROR in der gleichen SET-Anweisung.  
  
## <a name="july-2011"></a>Vom Juli 2011  
Die vom Juli 2011-Version von SSMA für Sybase enthält die folgenden Änderungen:  
  
-   Verbesserte fehlerberichterstellung während der Datenmigration.  
  
## <a name="april-2011"></a>April 2011  
Die April 2011-Version von SSMA für Sybase enthält die folgenden Änderungen:  
  
-   Konsolidierte "SSMA für Sybase"-Produkt, das unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali" und Azure SQL.  
-   Unterstützung für eine Verbindung herstellen und die Migration zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali".  
-   Eine neue Funktion zum Konvertieren und Migrieren von Sybase-Datenbanken in Azure SQL hinzugefügt.  
-   Verbesserte clientseitige Data Migration-Modul mit Unterstützung parallele Migration von Daten.  
-   Verbesserte Migration datenleistung mit einfachen und Bulk protokolliert Wiederherstellungsmodelle.  
-   Die Möglichkeit, um ordnungsgemäß zu konvertieren und Migrieren von Sybase-Datenbanken, die Groß-/Kleinschreibung beachtet, Groß-/Kleinschreibung von SQL Server hinzugefügt.  
-   Unterstützung für die Konvertierung von Sybase ASE-nicht-ANSI-Join-Anweisungen für SQL Server-ANSI-Join-Anweisungen hinzugefügt wurde erweitert, um das Löschen und UPDATE-Anweisungen.  
-   Zusätzliche Verbindungsoptionen für die Verbindung mit Sybase ASE-Server mithilfe von Sybase ASE-ODBC-Anbieter und Sybase ASE ADO.NET-Anbieter wird bereitgestellt.  
-   Entfernt die Abhängigkeit auf einer separaten Datenbank mit dem Namen **SysDB**, die die Sybase-Emulation-Funktionen (installiert als Teil des Erweiterungspaket) enthält.  
-   Die Möglichkeit zum Installieren von SSMA für Sybase-Erweiterungspaket auf hinzugefügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clustern.  
-   Abwärtskompatibilität von Projekten, die mit früheren Versionen von SSMA (v4. 0 und v4. 2) erstellten hinzugefügt.  
-   Die Möglichkeit zum Installieren von SSMA für Sybase V5. 0-Produkt Side-by-Side (SxS) mit älteren Versionen von SSMA (v4. 0 und v4. 2) wurde hinzugefügt.  
  
## <a name="july-2010"></a>Juli 2010  
Die Version vom Juli 2010 von SSMA für Sybase enthält die folgenden Änderungen:  
  
-   Unterstützung für die Migration zu SQL Server 2008 R2.  
-   Eine neue Anwendung der SSMA-Konsole für die Ausführung über die Befehlszeile wird hinzugefügt.  
-   Unterstützung für die Datenmigration mit serverseitigen und clientseitigen Data Migration-Engines.  
-   Unterstützung für "Benutzerdefinierte SELECT"-Anweisung in der Datenmigration.  
-   Unterstützung für die Migration von Sybase ASE 15.0.3 und 15.5.  
  
## <a name="june-2008"></a>Juni 2008  
Die Juni 2008-Version von SSMA für Sybase enthält die folgenden Änderungen:  
  
-   Hinzugefügte SSMA-Tester, der getestet wird automatisch die Konvertierung der Datenbank-Objekt und die Datenmigration von SSMA vorgenommen. Können Sie SSMA-Tester, nachdem alle Schritte zur Datenmigration SSMA abgeschlossen sind, stellen Sie sicher, dass die konvertierten Objekte die gleiche Weise funktioniert und alle Daten ordnungsgemäß übertragen wurde.  
-   Vorgängerversionen von SQL-Konvertierung hinzugefügt. Benutzer kann jetzt temporäre Tabelle (und andere Objekte) angeben Deklarationen für jede Quelle-Prozedur, die in der Konvertierung verwendet werden.  
-   Verbesserungen im objektkonvertierung hinzugefügt:  
    -   Verknüpft die Konvertierung überarbeitet.  
    -   Aggregate und nicht-Aggregate ohne-müssen/Group by-Klauseln.  
    -   Die IDENTITY-Funktion mit SELECT INTO-Anweisung.  
    -   Gruppierter Einschränkungen und Indizes auf Daten nur gesperrt.  
    -   Temporäre Tabellen, die von SELECT INTO erstellt werden.  
    -   Einschränkungen / Indizes für temporäre Tabellen.  
    -   Neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 Datetime-Typen werden unterstützt.  
    -   Unterstützung von Sybase-15.0-Konnektivität und Datentypen.  
  
## <a name="may-2007"></a>Mai 2007  
Veröffentlichung von Mai 2007 von SSMA für Sybase enthält die folgenden Änderungen:  
  
-   Die Möglichkeit Datenbankinhalt schneller zu laden, Speichern eines Projekts hinzugefügt.  
-   Unterstützung für die eingegebenen Kommentare in der SQL Server formatiert SQL-Modus.  
-   Verbesserungen im objektkonvertierung hinzugefügt.  
  
Die Hilfedatei wurde nicht für diese Version aktualisiert. Weitere Informationen finden Sie im Abschnitt "Hinweise zur Dokumentation" weiter unten in diesem Artikel.  
  
## <a name="november-2006"></a>November 2006  
Die Version vom November 2006 von SSMA für Sybase enthält die folgenden Änderungen:  
  
-   Neue globale Einstellungen wird hinzugefügt:  
    -   Wahlweise können Sie zum Anzeigen von Zeilennummern im Editor-Fenstern.  
    -   Sie können konfigurieren SSMA aufgefordert werden, um doppelte Objekte zu ersetzen, oder Sie können immer oder niemals, ersetzen doppelte Objekte während der schemakonvertierung.  
-   Eine neue Konvertierungsoption, mit dem Sie konfigurieren, wie die folgenden Situationen von SSMA verarbeitet wird hinzugefügt:  
    -   Eine CAST oder CONVERT-Anweisung, die eine binäre Zeichenfolge enthält.  
    -   Überprüft, ob null-Werte in Gleichheitsausdrücke.  
    -   Proxy-Tabellen.  
    -   Benutzer Fehler Meldungsnummern für RAISERROR.  
    -   UPDATE-Anweisungen, die nicht aufgelöste Bezeichner enthalten.  
-   Fügt eine neue Migrationsoption, mit dem Sie angeben, wie SSMA Datumsangaben verarbeiten soll, die außerhalb der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datumsbereich.  
-   Hinzugefügt eine **formatiert SQL** festlegen, auf die **SQL** Registerkarte, die den Code zur besseren Lesbarkeit formatiert.  
-   Aufgrund von Fehlerbehebungen, einschließlich:  
    -   SSMA konvertiert nun LOCK TABLE *Tabelle* IN {SHARED | EXKLUSIVE} Modus Anweisungen durch Hinzufügen einer TABLOCK oder TABLOCKX-Hinweises in der nachfolgenden SELECT-Abfrage für die Tabelle.  
    -   Die erforderlichen Umwandlungen werden nun hinzugefügt, wenn Binärtypen in Zeichen-Ausdrücke verwendet werden.  
    -   Verbesserungen der Arbeitsspeicher- und Leistungsproblemen.  
  
## <a name="july-2006"></a>Juli 2006  
Die Version von Juli 2006 von SSMA für Sybase war die erste Version.  
  
## <a name="see-also"></a>Siehe auch  
[Erste Schritte mit SSMA für Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
