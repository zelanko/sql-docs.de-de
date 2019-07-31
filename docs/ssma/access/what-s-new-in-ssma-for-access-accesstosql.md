---
title: Neues in SSMA für Access (Access Token SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 07/31/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: a24d3fc0-6911-4bfa-828a-197abf222e02
author: HJToland3
ms.author: Shamikg
ms.openlocfilehash: 39f8d7da95fc8e2102d1208216a2eb43bb038fea
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68632069"
---
# <a name="whats-new-in-ssma-for-access-accesstosql"></a>Neues in SSMA für Access (Access Token SQL)

In diesem Artikel wird SQL Server Migration Assistant (SSMA) für Zugriffs Änderungen in jeder Version aufgeführt.  

## <a name="ssma-v83"></a>SSMA v 8.3

Das v 8.3-Release von SSMA für Access wurde durch gezielte Korrekturen verbessert, die zur Verbesserung der Qualität und der konvertierungsmetriken entwickelt wurden. Außerdem bietet diese Version von SSMA für den Zugriff Korrekturen, die Folgendes bietet:

* Behandeln von Problemen mit Barrierefreiheit
* Grundlegende Unterstützung für den Typ "hierarchyid" in SQL Server hinzufügen

> [!IMPORTANT]
> Bei SSMA Version 7.4 und höheren Versionen ist .NET 4.5.2 eine erforderliche Installation.

## <a name="ssma-v82"></a>SSMA v 8.2

Die Version 8.2 von SSMA für Access wurde durch gezielte Korrekturen ergänzt, die zur Verbesserung der Qualität und der konvertierungsmetriken entwickelt wurden.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung kann zu einem Fehler bei einem Update von SSMA v 8.1 auf v 8.2 führen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter, und installieren Sie Sie manuell.

> [!IMPORTANT]
> Bei SSMA Version 7.4 und höheren Versionen ist .NET 4.5.2 eine erforderliche Installation.

## <a name="ssma-v81"></a>SSMA v 8.1

Die Version 8.1 von SSMA für Access wurde durch gezielte Korrekturen ergänzt, die zur Verbesserung der Qualität und der konvertierungsmetriken entwickelt wurden.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung kann zu einem Fehler bei einem Update von SSMA v 8.0 auf v 8.1 führen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter, und installieren Sie Sie manuell.

## <a name="ssma-v80"></a>SSMA v 8.0

Das v 8.0-Release von SSMA für Access wurde durch gezielte Korrekturen verbessert, die zur Verbesserung der Qualität und der konvertierungsmetriken entworfen wurden. Diese Version bietet auch die folgenden neuen Features:

* Unterstützung für **verwaltete Azure SQL-Datenbank-Instanz** als Ziel. Sie können jetzt neue Projekte erstellen, die auf verwaltete Azure SQL-Datenbank-Instanz abzielen:

  ![SQL-DB-Mi-Projekt](../media/ssma-newproject-sqldbmi.png)

* **Korrektur Ratgeber**nach der Konvertierung. Weitere Informationen hierzu [finden Sie hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbank/Schema-Auswahl.

    Beim Herstellen einer Verbindung mit der Quelle kann der Benutzer jetzt Datenbanken/Schemas von Interesse auswählen. Wenn Sie nur die Schemas auswählen, für die die Migration geplant ist, sparen Sie Zeit während der ersten Verbindung und verbessern die SSMA-Gesamtleistung.

   ![SSMA-Filter Objekte](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v 7.10

Das v 7.10-Release von SSMA für Access wurde durch gezielte Korrekturen verbessert, um zusätzliche Sicherheits-und Datenschutz Maßnahmen zum erfüllen von Änderungen an globalen Anforderungen bereitzustellen.

## <a name="ssma-v79"></a>SSMA v 7.9

Die Version Version 7.9 von SSMA für Access enthält die folgenden Änderungen:

* Gezielte Korrekturen, die Qualitäts-und konvertierungsmetriken verbessern.
* Unterstützung in der SSMA-Befehlszeile, um Datentyp Zuordnung und Projekteinstellungen zu ändern.
* Das Azure SQL-Daten bankverbindungs Dialogfeld in SSMA wurde ebenfalls geändert, um den voll qualifizierten Servernamen anzugeben. In früheren Versionen von SSMA musste das Azure SQL-Daten Bank Präfix in den Projekteinstellungen explizit angegeben werden.

## <a name="ssma-v78"></a>SSMA v 7.8

Das Release v 7.8 von SSMA für Access enthält die folgenden Änderungen:

* Ändern Sie in den Projekteinstellungen hervorgehobene Typzuordnung.
* Die Möglichkeit für Benutzer, Telemetriedaten zu deaktivieren.

## <a name="ssma-v77"></a>SSMA v 7.7

Die Version 7.7 von SSMA für Access enthält die folgenden Änderungen:

* Gezielte Korrekturen, die Qualitäts-und konvertierungsmetriken verbessern.
* Basierend auf der beliebten Nachfrage ist die 32-Bit-Version von SSMA für den Zugriff auf zurück. Im Vergleich zur vorherigen Implementierung (vor v 7.4) gibt es zwei Installer-Pakete, aber Sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version basierend auf den Konnektivitätskomponenten auswählen, die Sie besitzen. Es ist immer ratsam, die 64-Bit-Version zu verwenden, wenn möglich.

## <a name="ssma-v76"></a>SSMA v 7.6

Die Version Version 7.6 von SSMA für Access wurde durch gezielte Korrekturen ergänzt, die Qualitäts-und konvertierungsmetriken sowie die Unterstützung für SQL Server 2017 (öffentliche Vorschau) verbessern. Unterstützung für SQL Server 2017 unter Windows und Linux befindet sich in der öffentlichen Vorschau Phase und sollte nicht für Produktions Migrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA v 7.5

Die Version 7.5 von SSMA für den Zugriff wurde durch mehrere Verbesserungen verbessert, um die Barrierefreiheit für Personen mit Behinderungen zu erhöhen.

## <a name="ssma-v74"></a>SSMA v 7.4

Die Version 7.4 von SSMA für Access enthält die folgenden Änderungen:

* Die Option **Abfrage Timeout** ist jetzt bei der Schema Objekt Ermittlung unter Quelle und Ziel verfügbar.

  ![Abfrage Timeout (Option)](../media/query-timeout_red.png)

* Die Qualitäts-und Konvertierungs Metrik wurde durch gezielte Korrekturen verbessert, basierend auf Kundenfeedback.

  > [!IMPORTANT]
  > .NET 4.5.2 ist eine Voraussetzung für die Installation von SSMA v 7.4. Ab Version 7.4 wird die 32-Bit-Version von SSMA nicht mehr unterstützt.

## <a name="ssma-v73"></a>SSMA v 7.3

Das Release v 7.3 von SSMA für Access enthält die folgenden Änderungen:

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

Die Version Version 7.2 von SSMA für Access enthält die folgenden Änderungen:

* Verbesserte Qualitäts-und Konvertierungs Metrik durch gezielte Korrekturen auf der Grundlage von Kundenfeedback.
* Telemetrie-Verbesserungen, um bessere Datenpunkte zur Behandlung von Kundenproblemen und zur Verbesserung der Konvertierungsraten von SSMA bereitzustellen.

## <a name="ssma-v71"></a>SSMA v 7.1

Die Version 7.1 von SSMA für Access enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 wird jetzt als Zielplattform für die Migration unterstützt. Diese Funktion befindet sich in der Technical Preview und unterstützt das Schema und die Daten Verschiebung für SQL Server-Zielserver.
* SSMA unterstützt jetzt automatische Updates, um die neueste Version von SSMA herunterzuladen, sobald Sie verfügbar ist.
* Installierbare SSMA-Binärdateien werden jetzt über Windows Installer-Paketdateien (MSI) übermittelt.

## <a name="may-2016"></a>Mai 2016

Die Version vom Mai 2016 von SSMA für Access enthält die folgenden Änderungen:  
  
* Offizieller Support für SQL Server 2016 hinzugefügt
* Die Installer-Überprüfung für .NET 2,0 wurde entfernt.
* Die Befehle "Projekt speichern" und "Projekt öffnen" für die SSMA-Konsole wurden korrigiert.
* Der Befehl "SecurePassword" wurde für die SSMA-Konsole korrigiert.
* Das zählen von Objekten für das anfängliche laden wurde korrigiert.
* Tabellendaten werden für den Zugriff auf Benutzeroberflächen-Registerkarten geladen.
* Fehler in globalen Einstellungen behoben. 

## <a name="march-2016"></a>2016. März

Die Vorschauversion von SSMA vom März 2016 für Access bietet Unterstützung für die Migration zu SQL Server 2016.  

## <a name="january-2016"></a>2016. Januar

Die Wartungsversion von SSMA vom Januar 2016 für den Zugriff enthält die folgenden Änderungen:  
  
* Korrigiert ungültige Funktion für den Standardwert eines GUID-Felds (RFC 3894811).  
* Fehler beim Importieren von Datensätzen in SQL-Datenbank (Azure) (RFC 4919573).  
* Menü Element "View Log" zu SSMA hinzugefügt (RFC 5706203).  
* Telemetrie hinzugefügt.
  
## <a name="july-2014"></a>2014. Juli

Die SSMA-Version vom Juli 2014 für Access enthält die folgenden Änderungen:  
  
* Verbesserte Azure SQL-DB-Code Konvertierung.  
* Die Erweiterungspaket Funktionalität wurde in das Schema verschoben, um Azure SQL-Datenbank zu unterstützen  
* Getestete Leistungsverbesserungen für Datenbanken mit mehr als 10.000 Objekten.  
* Verbesserungen der Benutzeroberfläche für den Umgang mit einer großen Anzahl von Objekten.  
* Unterstützung für die Hervorhebung von bekannten Lob-Schemas hinzugefügt (sodass Sie bei der Konvertierung ignoriert werden können).  
* Zusätzliche Verbesserungen der Konvertierungsgeschwindigkeit
* Unterstützung für die Anzeige der Objekt Anzahl in der Benutzeroberfläche hinzugefügt
* Reduzierte Berichts Größe um mehr als 25%.
* Verbesserte Fehlermeldungen für nicht analysierte Konstrukte.  
  
## <a name="april-2014"></a>2014. April

Die SSMA-Version vom April 2014 für Access enthält die folgenden Änderungen:  
  
* Unterstützung für MS SQL Server 2014 hinzugefügt.
* Fehler bei der Konvertierung in Azure korrigiert.  
* Fehler in Bezug auf unsichtbare Berichts Seiten in IE 10 behoben.  
  
## <a name="january-2012"></a>2012. Januar

Die Version vom Januar 2012 von SSMA für Access enthält die folgenden Änderungen:  
  
* Gibt an, dass der Benutzername und das Kennwort für mit MS Access verknüpfte Tabellen nach der Migration nicht beibehalten werden  
* Legen Sie CASCADE-Aktionen für zirkuläre Verweise auf No action fest.  
* Bereitgestellte korrekte Meldungen, die angeben, dass CASCADE-Aktionen für Zirkel Verweise auf No action festgelegt wurden.  
  
## <a name="july-2011"></a>2011. Juli

Die Version vom Juli 2011 von SSMA für Access fügt eine verbesserte Fehlerberichterstattung während der Datenmigration hinzu.  
  
## <a name="april-2011"></a>2011. April

Die SSMA-Version vom April 2011 für Access enthält die folgenden Änderungen:  
  
* Es wurde ein einzelnes installier bares Element "SSMA for Access" hinzu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gefügt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , 2008, "Denali" und Azure SQL unterstützt.  
* Die Möglichkeit zum Herstellen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung mit "Denali" wurde hinzugefügt.  
* SSMA wurde für die Unterstützung der Zugriffs Konsolenversion für die Abwärtskompatibilität hinzugefügt. Sie können die Projekte öffnen, die von früheren Versionen von SSMA v 5.0 erstellt wurden.
* Es wurde die Möglichkeit hinzugefügt, das SSMA v 5.0-Produkt nebeneinander (SxS) mit älteren Versionen des SSMA-Produkts zu installieren.  
  
## <a name="july-2010"></a>2010. Juli  
Die SSMA-Version vom Juli 2010 für Access enthält die folgenden Änderungen:  
  
* Unterstützung für die Migration zu SQL Server 2008 R2 und Azure SQL hinzugefügt.
* Es wurde eine sichere Verbindung zu SQL Server und Azure SQL hinzugefügt.  
* Unterstützung für Access 2010-Datenbanken hinzugefügt.
* Es wurde eine neue SSMA-Konsolenanwendung für die Befehlszeilen Ausführung hinzugefügt.
* Unterstützung für den Datentyp "SQL Server datetime2" wurde hinzugefügt.
  
## <a name="june-2008"></a>2008. Juni

Die Version vom Juni 2008 von SSMA für Access bietet Unterstützung für den Zugriff auf 2007-Datenbanken.  
  
## <a name="may-2007"></a>Mai 2007

Die Version vom Mai 2007 von SSMA für Access enthält die folgenden Änderungen:  
  
* Unterstützung für Access-Datenbanken mit Arbeitsgruppen Richtlinien hinzugefügt.  
* Bietet die Möglichkeit, konvertierte Objekte aus dem SQL Server Metadaten-Explorer zu löschen.  
* Unterstützung für vom Benutzer eingegebene Kommentare im SQL Server formatierten SQL-Modus hinzugefügt.  
* Zusätzliche Verbesserungen bei der Objekt Konvertierung.  
  
## <a name="november-2006"></a>2006. November

Die SSMA-Version vom November 2006 für Access enthält die folgenden Änderungen:  
  
* Sie haben einen neuen Datenbankmigrations-Assistenten hinzugefügt, der Sie durch die Migration einer einzelnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Datenbank vom Zugriff auf führt.  
* Es wurde ein neuer Konvertierungs-, Lade-und Migrations Befehl hinzugefügt, der Zugriffs Datenbanken konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die konvertierten Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lädt und Daten in einem Schritt in alle migriert.  
* Verbesserte Abfrage Migration. Bei der Abfrage Migration werden nun weitere SELECT-Abfragen in Sichten konvertiert. Weitere Informationen finden Sie unter [umstellen von Access-Datenbankobjekten](converting-access-database-objects-accesstosql.md).  
* Die Möglichkeit zum Bearbeiten von Tabellen-und Index Eigenschaften auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Registerkarte **Tabelle** wurde hinzugefügt.  
* Neue globale Einstellungen hinzugefügt:
  * Sie können die Zeilennummern in Editor Fenstern anzeigen.  
  * Sie können SSMA so konfigurieren, dass doppelte Objekte ersetzt werden oder bei der Schema Konvertierung immer doppelte Objekte ersetzt werden.  
* Es wurde eine neue Konvertierungs Option hinzugefügt, mit der Sie angeben können, ob SSMA eine Warnung anzeigt, wenn eine komplexe Abfrage einen Platzhalter enthält.  
  
## <a name="july-2006"></a>2006. Juli

Die Version vom Juli 2006 von SSMA für Access war die erste Version.
