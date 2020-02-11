---
title: Neues in SSMA für SAP ASE (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/22/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
author: HJToland3
ms.author: Shamikg
ms.openlocfilehash: 752c099f985cc1695ab30e2d01241aea4c0c754c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "76516615"
---
# <a name="whats-new-in-ssma-for-sap-ase-sybasetosql"></a>Neues in SSMA für SAP ASE (sybasedesql)

In diesem Artikel werden die Änderungen an SQL Server Migration Assistant (SSMA) für SAP ASE (ehemals SSMA für Sybase) in jeder Version aufgeführt.

## <a name="ssma-v86"></a>SSMA v 8.6

Zusätzlich zu einem Zielsatz von Korrekturen, die zur Verbesserung der Benutzerfreundlichkeit und Leistung entwickelt wurden, wurde die Version Version 8.6 von SSMA für SAP ASE durch Hinzufügen einer Einstellung verbessert, mit der Benutzer die erweiterten SSMA-Eigenschaften im konvertierten Code weglassen können.

Um diese Einstellung zu nutzen, **Navigieren Sie in** > SSMA für SAP ASE zu Extras**Projekteinstellungen** > **Allgemeine** > **Konvertierung**, und aktualisieren Sie **dann unter "** Verschiedenes" den Wert der Einstellung " **Erweiterte Eigenschaften** unterdrücken" auf " **Ja**".

![Einstellung für erweiterte Eigenschaften weglassen](../sybase/media/ssma-omit-extended-properties.png)

> [!IMPORTANT]
> Mit SSMA Version 8.5 und höher ist .NET 4.7.2 eine erforderliche Installation. Wenn Sie diese Version installieren müssen, können Sie die Lauf Zeit Datei [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v85"></a>SSMA v 8.5

Die Version Version 8.5 von SSMA für SAP ASE wurde mit Unterstützung für Azure Active Directory Authentifizierung und grundlegender Unterstützung für JSON-Funktionen in SQL Server erweitert, sowie eine Reihe gezielter Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung.

Darüber hinaus können Sie mit SSMA für SAP ASE nun Systemtabellen und-Sichten ausblenden (von der Konvertierung ausschließen).

> [!IMPORTANT]
> Mit SSMA v 8.5 ist .NET 4.7.2 eine Installation, die Voraussetzung ist. Wenn Sie diese Version installieren müssen, können Sie die Lauf Zeit Datei [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v84"></a>SSMA v 8.4

Die Version Version 8.4 von SSMA für SAP ASE wurde durch gezielte Korrekturen ergänzt, die zur Behebung von Problemen bei der Barrierefreiheit entwickelt wurden, und zum Beheben eines Fehlers im Zusammenhang mit den maximalen Index Spalten (um 32 anstelle von 16) für SQL Server 2016 und höhere Versionen zuzulassen.

> [!IMPORTANT]
> Bei den SSMA-Versionen 7,4 bis 8,4 ist .NET 4.5.2 eine erforderliche Installation.

## <a name="ssma-v83"></a>SSMA v 8.3

Das v 8.3-Release von SSMA für SAP ASE wurde durch gezielte Korrekturen ergänzt, die zur Verbesserung der Qualität und der konvertierungsmetriken entwickelt wurden. Außerdem bietet diese Version von SSMA für SAP ASE Korrekturen, die Folgendes beinhaltet:

* Behandeln von Problemen mit Barrierefreiheit
* Grundlegende Unterstützung für den Typ "hierarchyid" in SQL Server hinzufügen

## <a name="ssma-v82"></a>SSMA v 8.2

Die Version 8.2 von SSMA für SAP ASE wurde durch eine Reihe von Korrekturen ergänzt, die zum Verbessern von Qualitäts-und konvertierungsmetriken entworfen wurden, sowie für folgende Korrekturen:

* Ein Problem mit deaktivierten, nicht gruppierten Indizes nach der Datenmigration.
* Erkennung von .NET Framework während der automatischen Installation.
* Ein zeitweiliger Absturz, der auftritt, wenn eine neue Version heruntergeladen wird.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung kann zu einem Fehler bei einem Update von SSMA v 8.1 auf v 8.2 führen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter, und installieren Sie Sie manuell.

## <a name="ssma-v81"></a>SSMA v 8.1

Die Version 8.1 von SSMA für SAP ASE wurde durch gezielte Korrekturen ergänzt, die zur Verbesserung der Qualität und der konvertierungsmetriken entwickelt wurden.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung kann zu einem Fehler bei einem Update von SSMA v 8.0 auf v 8.1 führen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter, und installieren Sie Sie manuell.

## <a name="ssma-v80"></a>SSMA v 8.0

Das v 8.0-Release von SSMA für SAP ASE wurde durch gezielte Korrekturen verbessert, die zur Verbesserung der Qualität und der konvertierungsmetriken entworfen wurden. Außerdem bietet diese Version die folgenden neuen Features:

* Unterstützung für **verwaltete Azure SQL-Datenbank-Instanz** als Ziel. Sie können jetzt neue Projekte erstellen, die auf verwaltete Azure SQL-Datenbank-Instanz abzielen:

  ![SQL-DB-Mi-Projekt](../media/ssma-newproject-sqldbmi.png)

* **Korrektur Ratgeber**nach der Konvertierung. Weitere Informationen hierzu [finden Sie hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbank/Schema-Auswahl.

  Beim Herstellen einer Verbindung mit der Quelle kann der Benutzer jetzt Datenbanken/Schemas von Interesse auswählen. Wenn Sie nur die Schemas auswählen, für die die Migration geplant ist, sparen Sie Zeit während der ersten Verbindung und verbessern die SSMA-Gesamtleistung.

  ![SSMA-Filter Objekte](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v 7.10

Das v 7.10-Release von SSMA für SAP ASE wurde durch gezielte Korrekturen verbessert, um zusätzliche Sicherheits-und Datenschutz Maßnahmen zum erfüllen von Änderungen an globalen Anforderungen bereitzustellen.

## <a name="ssma-v79"></a>SSMA v 7.9

Die Version Version 7.9 von SSMA für SAP ASE enthält die folgenden Änderungen:

* Gezielte Korrekturen, die Qualitäts-und konvertierungsmetriken verbessern.
* Unterstützung in der SSMA-Befehlszeile, um Datentyp Zuordnung und Projekteinstellungen zu ändern.
* Unterstützung für das Migrieren von Daten mithilfe von SQL Server Integration Services (SSIS). Nach dem Umrechnen des Schemas ist es möglich, ein SSIS-Paket zu erstellen, indem Sie mit der rechten Maustaste auf die Kontextmenü Option klicken.
* Das Azure SQL-Daten bankverbindungs Dialogfeld in SSMA wurde ebenfalls geändert, um den voll qualifizierten Servernamen anzugeben. In früheren Versionen von SSMA musste das Azure SQL-Daten Bank Präfix in den Projekteinstellungen explizit angegeben werden.

## <a name="ssma-v78"></a>SSMA v 7.8

Das Release v 7.8 von SSMA für SAP ASE enthält die folgenden Änderungen:

* Ändern Sie in den Projekteinstellungen hervorgehobene Typzuordnung.
* Die Möglichkeit für Benutzer, Telemetriedaten zu deaktivieren.

## <a name="ssma-v77"></a>SSMA v 7.7

Die Version Version 7.7 von SSMA für SAP ASE enthält die folgenden Änderungen:

* SSMA für SAP ASE wurde durch gezielte Korrekturen verbessert, die Qualitäts-und konvertierungsmetriken verbessern.
* Basierend auf der beliebten Nachfrage ist die 32-Bit-Version von SSMA für SAP ASE wieder verfügbar. Im Vergleich zur vorherigen Implementierung (vor v 7.4) gibt es zwei Installer-Pakete, aber Sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version basierend auf den Konnektivitätskomponenten auswählen, die Sie besitzen. Es ist immer ratsam, die 64-Bit-Version zu verwenden, wenn möglich.

## <a name="ssma-v76"></a>SSMA v 7.6

Die Version Version 7.6 von SSMA für SAP ASE enthält die folgenden Änderungen:

* Gezielte Korrekturen, die Qualitäts-und konvertierungsmetriken und Unterstützung für SQL Server 2017 (öffentliche Vorschau) verbessern. Unterstützung für SQL Server 2017 unter Windows und Linux befindet sich in der öffentlichen Vorschau Phase und sollte nicht für Produktions Migrationen verwendet werden.
* Unterstützung für die Konvertierung von Sybase-Funktionen.

## <a name="ssma-v75"></a>SSMA v 7.5

Das Release v 7.5 von SSMA für SAP ASE (ehemals SSMA für Sybase) enthält die folgenden Änderungen:

* Mehrere Verbesserungen, um mehr Barrierefreiheit für Menschen mit Behinderungen sicherzustellen.
* Unterstützung für die CREATE-oder REPLACE-Syntax.

## <a name="ssma-v74"></a>SSMA v 7.4

Die Version Version 7.4 von SSMA für Sybase enthält die folgenden Änderungen:

* Die Option **Abfrage Timeout** ist jetzt bei der Schema Objekt Ermittlung unter Quelle und Ziel verfügbar.

  ![Abfrage Timeout (Option)](../media/query-timeout_red.png)
* Die Qualitäts-und Konvertierungs Metrik wurde durch gezielte Korrekturen verbessert, basierend auf Kundenfeedback.

  > [!IMPORTANT]
  > .NET 4.5.2 ist eine Voraussetzung für die Installation von SSMA v 7.4. Außerdem wird ab Version 7.4 die 32-Bit-Version von SSMA eingestellt.  

## <a name="ssma-v73"></a>SSMA v 7.3

Das Release v 7.3 von SSMA für Sybase enthält die folgenden Änderungen:

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

Die Version Version 7.2 von SSMA für Sybase enthält die folgenden Änderungen:

* Verbesserte Qualitäts-und Konvertierungs Metrik durch gezielte Korrekturen auf der Grundlage von Kundenfeedback.
* Telemetrie-Verbesserungen, um bessere Datenpunkte zur Behandlung von Kundenproblemen und zur Verbesserung der Konvertierungsraten von SSMA bereitzustellen.

## <a name="ssma-v71"></a>SSMA v 7.1

Die Version Version 7.1 von SSMA für Sybase enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 wird jetzt als Zielplattform für die Migration unterstützt. Diese Funktion befindet sich in der Technical Preview und unterstützt das Schema und die Daten Verschiebung für SQL Server-Zielserver.
* Unterstützung für automatische Updates, um die neueste Version von SSMA herunterzuladen, sobald Sie verfügbar ist.
* Installierbare SSMA-Binärdateien werden jetzt über Windows Installer Paketdateien (MSI) übermittelt.

## <a name="may-2016"></a>Mai 2016

Die Version vom Mai 2016 von SSMA für Sybase enthält die folgenden Änderungen:  

* Unterstützung für SQL Server 2016 hinzugefügt.
* Die Installer-Überprüfung für .NET 2,0 wurde entfernt.
* Aktualisierte Extension Pack-Abhängigkeit von .NET 3,5 zu .NET 4,0.
* Die Befehle "Projekt speichern" und "Projekt öffnen" für die SSMA-Konsole wurden korrigiert.
* Der Befehl "SecurePassword" wurde für die SSMA-Konsole korrigiert.
* Das zählen von Objekten für das anfängliche laden wurde korrigiert.
* Fehler in globalen Einstellungen behoben.

## <a name="march-2016"></a>März 2016

Die Vorschauversion von SSMA vom März 2016 für Sybase bietet Unterstützung für die Migration zu SQL Server 2016.  
  
## <a name="january-2016"></a>Januar 2016

Die Wartungsversion von SSMA für Sybase vom Januar 2016 enthält die folgenden Änderungen:  
  
* Menü Element "View Log" zu SSMA hinzugefügt (RFC 5706203).  
* Telemetrie hinzugefügt.

## <a name="july-2014"></a>2014. Juli

Die SSMA-Version vom Juli 2014 für Sybase enthält die folgenden Änderungen:  
  
* Verbesserte Azure SQL-DB-Code Konvertierung.  
* Die Erweiterungspaket Funktionalität wurde in das Schema verschoben, um Azure SQL-Datenbank zu unterstützen  
* Hinzugefügte Leistungsverbesserungen für Datenbanken mit mehr als 10.000 Objekten.  
* Verbesserungen der Benutzeroberfläche für den Umgang mit einer großen Anzahl von Objekten.  
* Es wurde die Möglichkeit hinzugefügt, bekannte Lob-Schemas hervorzuheben (sodass Sie bei der Konvertierung ignoriert werden können).  
* Zusätzliche Verbesserungen der Konvertierungsgeschwindigkeit  
* Die Möglichkeit zum Anzeigen der Objekt Anzahl in der Benutzeroberfläche wurde hinzugefügt.
* Reduzierte Berichts Größe um mehr als 25%.  
* Verbesserte Fehlermeldungen für nicht analysierte Konstrukte.  
  
## <a name="april-2014"></a>April 2014

Die SSMA-Version vom April 2014 für Sybase enthält die folgenden Änderungen:  
  
* Unterstützung von MS SQL Server 2014 hinzugefügt.  
* Fehler bei der Konvertierung in Azure korrigiert.  
* Fehler in Bezug auf unsichtbare Berichts Seiten in IE 10 behoben.  
  
## <a name="january-2012"></a>Januar 2012

Die Version vom Januar 2012 von SSMA für Sybase enthält die folgenden Änderungen:  
  
* Unterstützung für Rollback-auslöserkonvertierung hinzugefügt
* Es wurde eine Korrektur zum@ROWCOUNT ändern von@ERROR @ und @ in derselben Set-Anweisung bereitgestellt.  
  
## <a name="july-2011"></a>Juli 2011

Die Version vom Juli 2011 von SSMA für Sybase bietet eine verbesserte Fehlerberichterstattung während der Datenmigration.  
  
## <a name="april-2011"></a>2011. April

Die SSMA-Version vom April 2011 für Sybase enthält die folgenden Änderungen:  
  
* Konsolidiertes "SSMA für Sybase"-Produkt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, "Denali" und Azure SQL unterstützt.  
* Unterstützung für das verbinden und Migrieren zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali" wurde hinzugefügt.  
* Es wurde ein neues Feature zum Konvertieren und Migrieren von Sybase-Datenbanken in Azure SQL hinzugefügt.  
* Verbessertes Client seitiges Daten Migrations Modul, das die parallele Migration von Daten unterstützt.  
* Verbesserte Daten Migrations Leistung durch einfaches und Massen protokolliertes Wiederherstellungs Modell.
* Die Möglichkeit zum ordnungsgemäßen konvertieren und Migrieren von Sybase-Datenbanken mit Berücksichtigung von Groß-und SQL Server Kleinschreibung wurde hinzugefügt.  
* Unterstützung für die Konvertierung von nicht-ANSI-JOIN-Anweisungen in Sybase-ASE in SQL Server ANSI JOIN-Anweisungen wurde für DELETE-und Update-Anweisungen erweitert.  
* Bietet zusätzliche Konnektivitätsoptionen zum Herstellen einer Verbindung mit Sybase-ASE-Servern mithilfe des Sybase ASE-ODBC-Anbieters und von Sybase-ASE ADO.net
* Die Abhängigkeit von einer separaten Datenbank namens **sysdb**, die die Sybase-Emulations Funktionen enthält (als Teil des Erweiterungspakets installiert), wurde entfernt.
* Die Möglichkeit zum Installieren von SSMA für das Sybase-Erweiterungs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Paket auf Clustern wurde hinzugefügt.
* Es wurde eine Abwärtskompatibilität von Projekten hinzugefügt, die in früheren Versionen von SSMA (v 4.0 und v 4.2) erstellt wurden.  
* Die Möglichkeit zur parallelen Installation von SSMA für Sybase v 5.0-Produkt mit älteren Versionen von SSMA (v 4.0 und v 4.2) wurde hinzugefügt.  
  
## <a name="july-2010"></a>Juli 2010

Die Version vom Juli 2010 von SSMA für Sybase wurde hinzugefügt:

* Unterstützung für die Migration zu SQL Server 2008 R2.  
* Eine neue SSMA-Konsolenanwendung für die Befehlszeilen Ausführung.  
* Unterstützung für die Datenmigration mithilfe von Server seitigen und Client seitigen Daten Migrations Modulen.  
* Unterstützung für die "Custom Select"-Anweisung bei der Datenmigration.  
* Unterstützung für die Migration von Sybase ASE 15.0.3 und 15,5.  
  
## <a name="june-2008"></a>2008. Juni

Die Version vom Juni 2008 von SSMA für Sybase enthält die folgenden Änderungen:  
  
* SSMA Tester hinzugefügt, der automatisch die Datenbankobjekt Konvertierung und die von SSMA vorgenommene Datenmigration testet. Nachdem alle SSMA-Migrations Schritte abgeschlossen sind, überprüfen Sie mithilfe von SSMA Tester, ob konvertierte Objekte auf dieselbe Weise funktionieren und dass alle Daten ordnungsgemäß übertragen wurden.
* Vor SQL-Konvertierung hinzugefügt. Der Benutzer kann jetzt temporäre Tabellen Deklarationen (und andere Objekt) für jede Quell Prozedur angeben, die bei der Konvertierung verwendet werden soll.
* Verbesserungen bei der Objekt Konvertierung:  
  * Die Joins wurden überarbeitet.  
  * Aggregate und nicht-Aggregate, ohne dass/GROUP BY-Klauseln vorhanden sind.  
  * Die IDENTITY-Funktion mit einer SELECT INTO-Anweisung.  
  * Gruppierte Einschränkungen und Indizes für Daten, die nur gesperrt sind.  
  * Temporäre Tabellen, die von SELECT INTO erstellt werden.  
  * Einschränkungen/Indizes für temporäre Tabellen.  
  * Neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 DateTime-Typen werden unterstützt.  
  * Unterstützung von Sybase 15,0-Konnektivität und-Datentypen.  
  
## <a name="may-2007"></a>Mai 2007

Die Version vom Mai 2007 von SSMA für Sybase wurde hinzugefügt:  
  
* Die Möglichkeit zum schnelleren Laden des Daten Bank Inhalts beim Speichern eines Projekts.  
* Unterstützung für vom Benutzer eingegebene Kommentare im SQL Server formatierten SQL-Modus.  
* Verbesserungen bei der Objekt Konvertierung.  

## <a name="november-2006"></a>2006. November

Die SSMA-Version vom November 2006 für Sybase enthält die folgenden Änderungen:  
  
* Neue globale Einstellungen hinzugefügt:  
  * Sie können die Zeilennummern in Editor Fenstern anzeigen.  
  * Sie können SSMA so konfigurieren, dass doppelte Objekte ersetzt werden oder bei der Schema Konvertierung immer doppelte Objekte ersetzt werden.  
* Es wurde eine neue Konvertierungs Option hinzugefügt, mit der Sie konfigurieren können, wie SSMA die folgenden Situationen behandelt:  
  * Eine CAST-oder Convert-Anweisung, die eine binäre Zeichenfolge enthält.  
  * Überprüft NULL-Werte in Gleichheits Ausdrücken.  
  * Proxy Tabellen.  
  * Fehlernummern der Benutzer Meldung für RAISERROR.  
  * Update-Anweisungen, die nicht aufgelöste Bezeichner enthalten.  
* Es wurde eine neue Migrations Option hinzugefügt, mit der Sie angeben können, wie SSMA Datums [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Angaben außerhalb des Datums Bereichs behandeln soll.  
* Auf der Registerkarte " **SQL** " wurde eine **formatierte SQL** -Einstellung hinzugefügt, die den Code für eine verbesserte Lesbarkeit formatiert.  
* Fehlerbehebungen, einschließlich:
  * SSMA konvertiert nun die Tabelle "Lock Table *" in {* Shared | Exklusive}-Modus-Anweisungen durch Hinzufügen eines TABLOCK-oder TABLOCKX-Hinweises zur nachfolgenden SELECT-Abfrage für die Tabelle.  
  * Die notwendigen Umwandlungen werden nun hinzugefügt, wenn binäre Typen in Zeichen Ausdrücken verwendet werden.  
  * Arbeitsspeicher-und Leistungsverbesserungen.  
  
## <a name="july-2006"></a>2006. Juli

Die Version von Juli 2006 von SSMA für Sybase war die erste Version.  
  
## <a name="see-also"></a>Weitere Informationen

[Informationen zu den ersten Schritten mit SSMA für Sybase &#40;sybasedesql&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
