---
title: Neuerungen in SSMA für Access (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 06/11/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: a24d3fc0-6911-4bfa-828a-197abf222e02
author: HJToland3
ms.author: Shamikg
ms.openlocfilehash: 50723f7b7161bbed960ce2f94e1b7bbf79d420d3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938413"
---
# <a name="whats-new-in-ssma-for-access-accesstosql"></a>Neuerungen in SSMA für Access (AccessToSQL)

Dieser Artikel führt SQL Server Migration Assistant (SSMA) für den Zugriff von Änderungen in jeder Version.  

## <a name="ssma-v82"></a>SSMA v8.2

Die v8.2-Version von SSMA für Access wird der gezielte Fixes erweitert, die entwickelt wurden, um die Qualität und Konvertierung von Metriken zu verbessern.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung möglicherweise den Fehler eines Updates aus SSMA v8. 1 auf v8.2. Wenn dieser Fehler auftritt, können herunterladen Sie die neue Version und installieren Sie ihn manuell klicken.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v81"></a>SSMA v8. 1

Die v8. 1-Version von SSMA für Access wird der gezielte Fixes erweitert, die entwickelt wurden, um die Qualität und Konvertierung von Metriken zu verbessern.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung möglicherweise den Fehler eines Updates von SSMA-Version 8.0 auf v8. 1. Wenn dieser Fehler auftritt, können herunterladen Sie die neue Version und installieren Sie ihn manuell klicken.

## <a name="ssma-v80"></a>SSMA v8. 0

Die v8. 0-Version von SSMA für Access wird erweitert, gezielte Fixes, die zur Verbesserung der Qualität und Konvertierung Metriken entwickelt. Diese Version bietet auch die folgenden neuen Features:

* Unterstützung für **Azure verwaltete SQL-Datenbankinstanz** als Ziel. Sie können jetzt neue Projekte, die für verwaltete Azure SQL-Datenbankinstanz erstellen:

  ![SQL-DB MI-Projekt](../media/ssma-newproject-sqldbmi.png)

* Nach der Konvertierung **Fix Advisor**. Weitere Informationen finden sie [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbankschema-Auswahl.

    Bei der Verbindung mit der Quelle kann der Benutzer nun Datenbanken oder Schemas, die von Interesse auswählen. Wählen nur die Schemas, die Sie migrieren möchten, wird die sparen Sie Zeit, während der ersten Verbindung und SSMA-gesamtleistung verbessern.

   ![SSMA Filtern von Objekten](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

Die v7.10-Version von SSMA für Access wird erweitert, gezielte Fixes soll, geben Sie zusätzliche Sicherheits- und Datenschutzfunktionen, um Änderungen in globalen Anforderungen zu erfüllen.

## <a name="ssma-v79"></a>SSMA v7.9

Die v7.9-Version von SSMA für Access umfasst die folgenden Änderungen:

* Gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern.
* Unterstützt die in der SSMA-Befehlszeile, Data Type Mapping und Projekt-Einstellungen zu ändern.
* Die Azure SQL-Datenbank-Verbindungsdialogfeld in SSMA wurde auch geändert, um den vollqualifizierten Servernamen angeben. In früheren Versionen von SSMA musste das Präfix für die Azure SQL-Datenbank innerhalb von Projekten Einstellungen angegeben werden.

## <a name="ssma-v78"></a>SSMA V7. 8

Die V7. 8-Version von SSMA für Access umfasst die folgenden Änderungen:

* Ändern Sie die Zuordnung eines Typs in den Projekteinstellungen hervorgehoben.
* Die Möglichkeit für Benutzer zum Deaktivieren der Telemetrie.

## <a name="ssma-v77"></a>SSMA v7.7

Die v7.7-Version von SSMA für Access umfasst die folgenden Änderungen:

* Gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern.
* Basierend auf der großen Nachfrage, ist der 32-Bit-Version von SSMA für Access zurück. Im Vergleich zu der vorherigen Implementierung (vor v7.4), es gibt zwei Installationspakete, aber sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version auf Grundlage der Konnektivitätskomponenten benötigen Sie auswählen. Es ist immer besser, nach Möglichkeit die 64-Bit-Version zu verwenden.

## <a name="ssma-v76"></a>SSMA v7.6

Die v7.6-Version von SSMA für Access wird erweitert, mit gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern und mit Unterstützung für SQL Server 2017 (öffentliche Vorschau). Unterstützung für SQL Server 2017 unter Windows und Linux wird in der öffentlichen Vorschau und darf nicht für Produktionsmigrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA V7. 5

Die V7. 5-Version von SSMA für Access wird durch verschiedene Verbesserungen, um sicherzustellen, dass größere Barrierefreiheit für Personen mit behinderungen erweitert.

## <a name="ssma-v74"></a>SSMA v7.4

Die v7.4-Version von SSMA für Access umfasst die folgenden Änderungen:

* Die **Abfragetimeout** Option ist während der Ermittlung an Quelle und Ziel am Schema jetzt verfügbar.

  ![Option Timeout für Remoteabfragen](../media/query-timeout_red.png)

* Die Qualität und Konvertierung-Metrik wurde durch gezielte Fixes, basierend auf Kundenfeedback verbessert.

  > [!IMPORTANT]
  > .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA-v7.4. Darüber hinaus v7.4 ab, die 32-Bit-Version von SSMA nicht mehr unterstützt.

## <a name="ssma-v73"></a>SSMA V7. 3

Die V7. 3-Version von SSMA für Access umfasst die folgenden Änderungen:

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

Die V7. 2-Version von SSMA für Access umfasst die folgenden Änderungen:

* Verbesserte Qualität und Konvertierung Metrik mit gezielte Fixes, die basierend auf Kundenfeedback.
* Telemetrie Erweiterungen besser Datenpunkte zum Behandeln von Kundenproblemen und Verbessern SSMAs-Abschlussraten bereit.

## <a name="ssma-v71"></a>SSMA v7.1

Die v7.1-Version von SSMA für Access umfasst die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Dieses Feature ist in der technischen Vorschau und unterstützt das Verschieben von Schema und Daten an SQL-Zielserver.
* SSMA unterstützt jetzt die automatische Updates für die neueste Version von SSMA herunterladen, sobald diese verfügbar ist.
* Installierbare SSMA-Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) übermittelt.

## <a name="may-2016"></a>Mai 2016

Die Mai 2016-Version von SSMA für Access umfasst die folgenden Änderungen:  
  
* Offizielle Unterstützung für SQL Server 2016
* Entfernt die Überprüfung der Installer für .net 2.0.
* Feste "Speichern" Projekt"und"Projekt öffnen"-Befehle für SSMA-Konsole.
* Feste "Securepassword"-Befehl für SSMA-Konsole.
* Korrektur von Objekten für das anfängliche laden zählen.
* Festen Tabellen Laden von Daten für die UI-Registerkarten für den Zugriff.
* Korrektur von Bug in den globalen Einstellungen. 

## <a name="march-2016"></a>März 2016

Die Preview-Version vom März 2016 von SSMA für Access fügt Unterstützung für die Migration zu SQL Server 2016.  

## <a name="january-2016"></a>Januar 2016

Die Version der Januar 2016 Wartung von SSMA für Access umfasst die folgenden Änderungen:  
  
* Fixed-ungültige Funktion für den Standardwert eines Felds der GUID (RFC 3894811).  
* Feste stürzt beim Importieren von Datensätzen in der SQL-Datenbank (Azure) (RFC 4919573) zu erhalten.  
* Hinzugefügte Ansicht der Protokoll-Menüelement, SSMA (RFC 5706203).  
* Zusätzliche Telemetriedaten.
  
## <a name="july-2014"></a>Juli 2014

Die Juli 2014-Version von SSMA für Access umfasst die folgenden Änderungen:  
  
* Verbesserte codekonvertierung für Azure SQL-Datenbank.  
* Extension-Pack-Funktion zum Schema zur Unterstützung von Azure SQL-Datenbank verschoben.  
* Getestete leistungsverbesserungen für Datenbanken mit mehr als 10 k-Objekte.  
* Zusätzliche Verbesserungen der Benutzeroberfläche für den Umgang mit großen Anzahl von Objekten.  
* Unterstützung für die Hervorhebung von "bekannte" LOB-Schemas (sodass sie bei der Konvertierung ignoriert werden können).  
* Geschwindigkeit der Konvertierung wird hinzugefügt.
* Unterstützung für das Objekt anzeigen wird in der Benutzeroberfläche.
* Reduzierte Berichtsgröße von mehr als 25 %.
* Verbesserte Fehlermeldungen für nicht verarbeitete Konstrukte.  
  
## <a name="april-2014"></a>April 2014

Die Version vom April 2014 von SSMA für Access umfasst die folgenden Änderungen:  
  
* Unterstützung für MS SQL Server 2014 hinzugefügt.
* Behobenen Problemen in Bezug auf die Konvertierung in Azure.  
* Behobenen Problemen in Bezug auf unsichtbare Berichtsseiten in Internet Explorer 10.  
  
## <a name="january-2012"></a>Januar 2012

Die Januar 2012-Version von SSMA für Access umfasst die folgenden Änderungen:  
  
* Die Möglichkeit, den Benutzernamen und das Kennwort nicht beibehalten, für die MS Access verknüpfte Tabellen nach der Migration wird bereitgestellt.  
* Legen Sie die Cascade-Aktionen für Zirkuläre Verweise auf No Action.  
* Sofern die richtige Nachrichten, der angibt, Cascade-Aktionen für Zirkuläre Verweise auf No Action festgelegt wurden.  
  
## <a name="july-2011"></a>Vom Juli 2011

Die vom Juli 2011-Version von SSMA für Access fügt verbesserte fehlerberichterstellung, die während der Datenmigration.  
  
## <a name="april-2011"></a>April 2011

Die April 2011-Version von SSMA für Access umfasst die folgenden Änderungen:  
  
* Hinzugefügt von einem einzelnen installierbaren "SSMA für Access", die unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali" und Azure SQL.  
* Die Fähigkeit zum Verbinden hinzugefügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali".  
* Hinzugefügte SSMA für Access-Konsole Version für die Abwärtskompatibilität unterstützen. Sie können die von früher in SSMA V5. 0-Versionen erstellte Projekte öffnen.
* Die Möglichkeit zum Installieren von SSMA V5. 0-Produkt parallele (SxS) mit älteren Versionen von SSMA-Produkt hinzugefügt.  
  
## <a name="july-2010"></a>Juli 2010  
Die Version vom Juli 2010 von SSMA für Access umfasst die folgenden Änderungen:  
  
* Unterstützung für die Migration zu SQL Server 2008 R2 und Azure SQL.
* SQL Server und Azure SQL hinzugefügt eine sichere Verbindung.  
* Unterstützung für Access 2010-Datenbanken.
* Eine neue Anwendung der SSMA-Konsole für die Ausführung über die Befehlszeile wird hinzugefügt.
* Unterstützung für SQL Server-DateTime2-Datentyp.
  
## <a name="june-2008"></a>Juni 2008

Die Juni 2008-Version von SSMA für Access fügt Unterstützung für Access 2007-Datenbanken hinzu.  
  
## <a name="may-2007"></a>Mai 2007

Veröffentlichung von Mai 2007 von SSMA für Access umfasst die folgenden Änderungen:  
  
* Unterstützung für den Zugriff auf Datenbanken, die Arbeitsgruppe Richtlinien verwenden.  
* Bereitgestellt, die Möglichkeit, die konvertierten Objekte aus dem Metadaten-Explorer von SQL Server zu löschen.  
* Unterstützung für die eingegebenen Kommentare in der SQL Server formatiert SQL-Modus.  
* Verbesserungen im objektkonvertierung hinzugefügt.  
  
## <a name="november-2006"></a>November 2006

Die Version vom November 2006 von SSMA für Access umfasst die folgenden Änderungen:  
  
* Hinzugefügt von einer neuen Datenbank-Migrations-Assistenten, die Sie aus den Zugriff auf die Migration von einer einzelnen Datenbank führt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
* Eine neue Convert, Load, hinzugefügt und Migrate-Befehl ab, der Zugriff auf Datenbanken, konvertiert lädt die konvertierten Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und Migrieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einem Schritt.  
* Verbesserte-Migration. Fragen Sie die Migration nun konvertiert mehr Abfragen mit Ansichten auswählen. Weitere Informationen finden Sie unter [den Zugriff auf Datenbankobjekte konvertieren](converting-access-database-objects-accesstosql.md).  
* Die Fähigkeit zum Bearbeiten der Eigenschaften von Tabellen und Indizes auf hinzugefügt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Tabelle** Registerkarte.  
* Neue globale Einstellungen wird hinzugefügt:
  * Wahlweise können Sie zum Anzeigen von Zeilennummern im Editor-Fenstern.  
  * Sie können konfigurieren SSMA aufgefordert werden, um doppelte Objekte zu ersetzen, oder Sie können immer oder niemals, ersetzen doppelte Objekte während der schemakonvertierung.  
* Hinzugefügt, eine neue Konvertierungsoption, mit dem Sie angeben, ob SSMA eine Warnung angezeigt, wenn eine komplexe Abfrage einen Platzhalter enthält.  
  
## <a name="july-2006"></a>Juli 2006

Die Version von Juli 2006 von SSMA für Access war die erste Version.
