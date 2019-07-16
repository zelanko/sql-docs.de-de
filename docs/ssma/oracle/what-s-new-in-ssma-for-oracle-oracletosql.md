---
title: Neuerungen in SSMA für Oracle (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 06/11/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
author: HJToland3
ms.author: Shamikg
ms.openlocfilehash: 20fc72ce649d8ab66c43fe1c8f3a87775d83f9fa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086779"
---
# <a name="whats-new-in-ssma-for-oracle-oracletosql"></a>Neuerungen in SSMA für Oracle (OracleToSQL)
In diesem Artikel werden die SQL Server Migration Assistant (SSMA) für Oracle-Änderungen in jeder Version aufgelistet.

## <a name="ssma-v82"></a>SSMA v8.2

Die v8.2-Version von SSMA für Oracle wird zum verbessert:

* Hinzufügen von Unterstützung für die Prozedur DBMS_OUTPUT. AKTIVIEREN ODER DEAKTIVIEREN.
* Entfernen Sie CAST AS "float" für BINARY_FLOAT und BINARY_DOUBLE Spalten im Data Migration-Abfrage.
* Beheben Sie Sequenzen aktualisieren, wenn der aktuelle Wert geändert wurde.
* Beheben Sie Fehler, die zur Fehlinterpretation von Pseudospalten (ROWNUM usw.), wenn eine Spalte mit dem gleichen Namen vorhanden ist.
* Korrektur eines Absturzes, das FOR-Schleifen mit mehrdeutiger nicht aufgelöster Bezeichner Konvertierung tritt ein, an.

Darüber hinaus enthält diese Version eine bestimmte Reihe von Fehlerbehebungen zur Verbesserung der Qualität und Konvertierung Metriken als auch Fehlerbehebungen für entwickelt:

* Ein Problem mit deaktivierten nicht gruppierten Indizes nach der Datenmigration.
* Erkennung von .NET Framework während der automatischen Installation.
* Eine vorübergehende Absturz, das auftritt, wenn eine neue Version heruntergeladen wird.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung möglicherweise den Fehler eines Updates aus SSMA v8. 1 auf v8.2. Wenn dieser Fehler auftritt, können herunterladen Sie die neue Version und installieren Sie ihn manuell klicken.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v81"></a>SSMA v8. 1

Gezielte Fixes wird die v8. 1-Version von SSMA für Oracle erweitert, die entwickelt wurden, zur Verbesserung der Qualität und Konvertierung von Metriken.

> [!NOTE]
> Ein bekanntes Problem bei der automatischen Aktualisierung möglicherweise den Fehler eines Updates von SSMA-Version 8.0 auf v8. 1. Wenn dieser Fehler auftritt, können herunterladen Sie die neue Version und installieren Sie ihn manuell klicken.

## <a name="ssma-v80"></a>SSMA v8. 0

Die v8. 0-Version von SSMA für Oracle wird erweitert, gezielte Fixes, die zur Verbesserung der Qualität und Konvertierung Metriken entwickelt. Diese Version bietet auch die folgenden neuen Features:

* Unterstützung für **Azure verwaltete SQL-Datenbankinstanz** als Ziel. Sie können jetzt neue Projekte, die für verwaltete Azure SQL-Datenbankinstanz erstellen:

  ![SQL-DB MI-Projekt](../media/ssma-newproject-sqldbmi.png)

  > [!NOTE]
  > SSMA für Oracle-Erweiterungspaket wurde ebenfalls aktualisiert, um die remote-Installationen auf Azure verwaltete SQL-Datenbankinstanz zu ermöglichen:
  >
  > ![SSMA für Oracle-Erweiterungspaket](../media/ssma-oracle-ext-pack.png)

  Einige Funktionen, einschließlich der Tester und serverseitige Datenmigration werden nicht unterstützt, wenn Azure verwaltete SQL-Datenbankinstanz. Erfahren Sie mehr über [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/migrate-your-oracle-database-to-azure-sql-database-managed-instance-using-ssma-8-0/).

* Nach der Konvertierung **Fix Advisor**. Weitere Informationen finden sie [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbankschema-Auswahl.

  Bei der Verbindung mit der Quelle kann der Benutzer nun Datenbanken oder Schemas, die von Interesse auswählen. Wählen nur die Schemas, die Sie migrieren möchten, wird die sparen Sie Zeit, während der ersten Verbindung und SSMA-gesamtleistung verbessern.

  ![SSMA Filtern von Objekten](../media/ssma-filter-objects.png)

* Die Möglichkeit, die offiziellen, von verwalteten NET-Treiber verwenden, um die Verbindung mit Oracle. Der OCI-Treiber ist nicht mehr eine erforderliche Komponente für die Verwendung von SQL Server Migration Assistant für Oracle.

* Die Fähigkeit, VARCHAR ROWID und UROWID standardmäßig zugeordnet. Wurde von 'Uniqueidentifier', um die Datenmigration für explizite ROWID-Spalten zu ermöglichen.

## <a name="ssma-v710"></a>SSMA v7.10

Die v7.10-Version von SSMA für Oracle enthält die folgenden Änderungen:

* Gezielte Fixes soll, geben Sie zusätzliche Sicherheits- und Datenschutzfunktionen, um Änderungen in globalen Anforderungen zu erfüllen.
* Eine Konvertierung-Verbesserung, die im Zusammenhang mit der hierarchische Abfragen.

## <a name="ssma-v79"></a>SSMA v7.9

Die v7.9-Version von SSMA für Oracle enthält die folgenden Änderungen:

* Gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern.
* Unterstützung für "Weiter"-Anweisungen von Oracle zu SQL Server migrieren.
* Unterstützt die in der SSMA-Befehlszeile, Data Type Mapping und Projekt-Einstellungen zu ändern.
* Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach der Konvertierung des Schemas ist es möglich, ein SSIS-Paket mit einer Option für das Kontextmenü zu erstellen.
* Die Azure SQL-Datenbank-Verbindungsdialogfeld in SSMA wurde auch geändert, um den vollqualifizierten Servernamen angeben. In früheren Versionen von SSMA musste das Präfix für die Azure SQL-Datenbank innerhalb von Projekten Einstellungen angegeben werden.

## <a name="ssma-v78"></a>SSMA V7. 8

Die V7. 8-Version von SSMA für Oracle enthält die folgenden Änderungen:

* Unterstützung für:
  * Der zeilenausdruck für die IN-Klausel.
  * Implizite Typumwandlungen.
  * UID-Konvertierung für Azure SQL-Datenbank.
* Ändern Sie die Zuordnung eines Typs in den Projekteinstellungen hervorgehoben.
* Die Möglichkeit für Benutzer zum Deaktivieren der Telemetrie.

## <a name="ssma-v77"></a>SSMA v7.7

Die v7.7-Version von SSMA für Oracle enthält die folgenden Änderungen:

* SSMA für Oracle wurde gezielte Fixes erweitert, die die Qualität und Konvertierung von Metriken zu verbessern.
* Basierend auf der großen Nachfrage, ist die 32-Bit-Version von SSMA für Oracle zurück. Im Vergleich zu der vorherigen Implementierung (vor v7.4), es gibt zwei Installationspakete, aber sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version auf Grundlage der Konnektivitätskomponenten benötigen Sie auswählen. Es ist immer besser, nach Möglichkeit die 64-Bit-Version zu verwenden.
* Unterstützung für SQL Server 2017 ist jetzt mit der Oracle-Erweiterungspaket auch unter Linux unterstützt (neue-remote-Installationsoption) offizielle. Beachten Sie, dass Erweiterungspaket-Funktionalität beschränkt ist, bei der Installation unter Linux, als der Tester und serverseitigen livemigrationsfunktionen werden nicht unterstützt.
* SSMA für Oracle ermöglicht, materialisierte Sichten als reguläre Tabellen migrieren (konfigurierbar über die Einstellungen auf **Projekteinstellungen** -> **Synchronisierung**  ->  **Unterstützenden Tabellen für materialisierte Sichten ermitteln**).

## <a name="ssma-v76"></a>SSMA v7.6

Die v7.6-Version von SSMA für Oracle wird erweitert, mit gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern und mit Unterstützung für SQL Server 2017 (öffentliche Vorschau). Unterstützung für SQL Server 2017 unter Windows und Linux wird in der öffentlichen Vorschau und darf nicht für Produktionsmigrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA V7. 5

Die Version 7.5 von SSMA für Oracle enthält die folgenden Änderungen:

* Durch zahlreiche Verbesserungen, um sicherzustellen, dass größere Barrierefreiheit für Personen mit behinderungen verbessert.
* Zur Verbesserung der Qualität und Konvertierung Metrik mit gezielte Fixes aktualisiert, wie z. B. verbesserte Behandlung von Datums-und "float", während der Datenmigration, basierend auf Kundenfeedback.

## <a name="ssma-v74"></a>SSMA v7.4

Die v7.4-Version von SSMA für Oracle enthält die folgenden Änderungen:

* SSMA für Oracle unterstützt jetzt die Azure SQL Data Warehouse als Zielplattform für die Migration.

  ![Fenster "Neues Projekt"](../media/new-project.png)
  * Unterstützt die Data Warehouse-Speicheroptionen, wie in der folgenden Abbildung gezeigt:

  ![Speicheroptionen für Datawarehouse](../media/storage-options_red.png)
  * Die Optionen für die Verteilung unterstützt, wie in der folgenden Abbildung gezeigt:

  ![Verteilung von Daten für Datawarehouse](../media/data-distribution_red.png)

* Die **Abfragetimeout** Option ist während der Ermittlung an Quelle und Ziel am Schema jetzt verfügbar.

  ![Option Timeout für Remoteabfragen](../media/query-timeout_red.png)

* Die Qualität und Konvertierung-Metrik wurde durch gezielte Fixes, basierend auf Kundenfeedback verbessert.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA-v7.4. Darüber hinaus wird v7.4 ab, die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v73"></a>SSMA V7. 3

Die V7. 3-Version von SSMA für Oracle enthält die folgenden Änderungen:

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

Die V7. 2-Version von SSMA für Oracle enthält die folgenden Änderungen:

* Verbesserte Qualität und Konvertierung Metrik mit gezielte Fixes, die basierend auf Kundenfeedback.
* Telemetrie Erweiterungen besser Datenpunkte zum Behandeln von Kundenproblemen und Verbessern SSMAs-Abschlussraten bereit.

## <a name="ssma-v71"></a>SSMA v7.1

Die v7.1-Version von SSMA für Oracle enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Dieses Feature ist in der technischen Vorschau und ermöglicht die Verlagerung von Schema und Daten an SQL-Zielserver.
* SSMA unterstützt jetzt die automatische Updates für die neueste Version von SSMA herunterladen, sobald diese verfügbar ist.
* Installierbare SSMA-Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) übermittelt.

## <a name="may-2016"></a>Mai 2016

Die Version Mai 2016 von SSMA für Oracle enthält die folgenden Änderungen:  

* Unterstützung für SQL Server 2016 hinzugefügt.
* Zusätzliche Konvertierung Oracle Flashback Archivtabellen in temporalen Tabellen mit SQL Server.

  > [!NOTE]
  > SSMA kopieren keine Verlaufsdaten aus Oracle Flashback Daten Archivtabellen. Daher müssen die Verlaufsdaten während der Migration manuell kopiert werden. Darüber hinaus können SSMA die Verlaufstabelle in die SQL Server-Metadaten-Explorer nicht angezeigt, da es als eine Systemtabelle behandelt wird, Sie die Verlaufstabelle in SQL Server Management Studio angezeigt werden.
  >
  > SQL Server 2016 unterstützt nicht mehrere Oracle Flashback-Funktionen, einschließlich:
  >
  > * Oracle Flashback Transaktion-Abfrage
  > * DBMS_FLASHBACK-Paket
  > * Flashback Transaktion
  > * Datenarchiv Flashback
  > * Flashback-Tabelle
  > * Flashback löschen
  > * Flashback Database
* Zusätzliche Konvertierung Oracle VPD-Richtlinie in SQL Server-Richtlinienobjekten (Sicherheit auf Zeilenebene für Oracle).
* Geringere Zeit des anfänglichen Ladevorgangs für Oracle.
* Verbesserte Parser und Auflösung.
* Entfernt die Überprüfung der Installer für .net 2.0.
* Aktualisierte Erweiterungspaket Abhängigkeit von .net 3.5 zu .net 4.0.
* Feste "Speichern" Projekt"und"Projekt öffnen"-Befehle für SSMA-Konsole.
* Feste "Securepassword"-Befehl für SSMA-Konsole.
* Korrektur von Objekten für das anfängliche laden zählen.
* Korrektur, Konvertieren von Zeichen-Datentypen für Oracle.
* Korrektur von Bug in den globalen Einstellungen.
  
## <a name="march-2016"></a>März 2016

Die Preview-Version vom März 2016 von SSMA für Oracle-Unterstützung für:  
  
* Migration zu SQLServer 2016.  
* Migrieren von Oracle Sicherheit auf Zeilenebene (mit gewissen Einschränkungen).  
* Migrieren von Oracle in Memory-Tabellen auf SQL Server-Spalte Store.  
  
## <a name="january-2016"></a>Januar 2016

Im Januar 2014 Wartung-Version von SSMA für Oracle enthält die folgenden Änderungen:  
  
* Unterstützung für gruppierte Indizes.  
* Korrektur von langsamen Abfragen für Oracle-Schemas (RFC 5076207).  
* Feste über die Konsole verbinden.  
* Hinzugefügte Ansicht der Protokoll-Menüelement, SSMA (RFC 5706203). 
* Zusätzliche Telemetriedaten.
  
## <a name="july-2014"></a>Juli 2014

Die Version von Juli 2014 von SSMA für Oracle enthält die folgenden Änderungen:  
  
* Unterstützung für Azure SQL-Datenbank hinzugefügt.
* Pack-Funktionalität von Erweiterungen, die in Schema zur Unterstützung von Azure SQL-Datenbank verschoben werden.
* Unterstützung für Oracle materialisierte Sichten hinzugefügt.  
* Unterstützung für die Arbeitsspeicher von SQL Server 2014 Speicheroptimierte Tabellen.  
* Leistungsverbesserungen enthalten, die für Datenbanken mit mehr als 10 KB Objekten getestet.  
* Zusätzliche Verbesserungen der Benutzeroberfläche für den Umgang mit großen Anzahl von Objekten.  
* Hinzugefügt, Hervorhebung von "bekannte" LOB-Schemas.  
* Enthalten die Geschwindigkeit der Konvertierung.  
* Unterstützung für das Objekt anzeigen wird in der Benutzeroberfläche.  
* Reduzierte Berichtsgröße von mehr als 25 %.
* Verbesserte Fehlermeldungen für nicht verarbeitete Konstrukte.  
  
## <a name="april-2014"></a>April 2014

Die Version vom April 2014 von SSMA für Oracle enthält die folgenden Änderungen:  
  
* Die Unterstützung von MS SQL Server 2014.  
* Die Unterstützung der Oracle-12 und Abfrage-Optimierung.  
* Behobenen Problemen in Bezug auf die Konvertierung in Azure.  
* Behobenen Problemen in Bezug auf unsichtbare Berichtsseiten in Internet Explorer 10.  
  
## <a name="january-2012"></a>Januar 2012

Die Januar 2012-Version von SSMA für Oracle bietet Unterstützung für RowType und Eingabeparameter "RecordType" standardmäßig auf NULL.  
  
## <a name="july-2011"></a>Vom Juli 2011

Die vom Juli 2011-Version von SSMA für Oracle enthält die folgenden Änderungen:  
  
* Unterstützung für die Konvertierung von Oracle-Sequenz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali" Sequenz-Generator.
* Verbesserte fehlerberichterstellung während der Datenmigration.  
* Verbesserte Konvertierung der Anweisung, die Verwendung reservierter Wörter.  
* Verbessert die implizite Konvertierung von Date-Wert in einer Funktion.  
  
## <a name="april-2011"></a>April 2011

Die April 2011-Version von SSMA für Oracle enthält die folgenden Änderungen:  
  
* Konsolidierte "SSMA für Oracle"-Produkt, das unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali".
* Unterstützung für eine Verbindung herstellen und die Migration zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali".  
* Verbesserte clientseitige Data Migration-Modul mit Unterstützung parallele Migration von Daten.  
* Verbesserte Migration datenleistung mit einfachen und Bulk protokolliert Wiederherstellungsmodelle.  
* Unterstützung für die Abwärtskompatibilität mit früheren Versionen von SSMA (v4. 0 und v4. 2) erstellten Projekten hinzugefügt.  
* Die Möglichkeit zum Installieren von SSMA für Oracle V5. 0-Produkt parallele (SxS) mit älteren Versionen von SSMA (v4. 0 und v4. 2) wurde hinzugefügt.
* Unterstützung für die berichterstellung, User-Defined Types (einschließlich Untertyp, SAMMLUNGSDATENTYPEN, GESCHACHTELTE Tabelle, Objekttabelle und Objektansicht) und deren Verwendung in PL/SQL-Blöcke mit speziellen Fehlermeldungen.  

## <a name="july-2010"></a>Juli 2010

Die Version vom Juli 2010 von SSMA für Oracle hinzugefügt:

* Unterstützung für die Migration zu SQL Server 2008 R2.  
* Eine neue SSMA-Konsolenanwendung für die Ausführung über die Befehlszeile.  
* Unterstützung für die Datenmigration mit serverseitigen und clientseitigen Data Migration-Engines.  
* Unterstützung für "Benutzerdefinierte SELECT"-Anweisung in der Datenmigration.  
* Unterstützung für die Migration von Oracle 11g R2.  
  
## <a name="june-2008"></a>Juni 2008

Die Juni 2008-Version von SSMA für Oracle enthält die folgenden Änderungen:  
  
* Der Bewertungsbericht, z. B. zusätzliche Informationen für Synonyme, unformatierte Quelle für auswertbare Objekte, Bereiche und SQL Server-Logo-Entfernung und layoutspeicherung Verbesserungen hinzugefügt.  
* Verbesserungen im objektkonvertierung hinzugefügt:  
  * Pakete DBMS_LOB, DBMS_SQL Konvertierung hinzugefügt.  
  * Verknüpft die Konvertierung überarbeitet.  
  * Änderung von Sammlungen und Datensätze Konvertierung, jetzt von Datensätzen in einfachen Fällen, die über separate Variablen für die einzelnen Felder veröffentlicht.  
  * Verbesserungen der Implementierung von Datensätzen und Sammlungen.  
  * Windowing-Aggregationsfunktionen hinzugefügt.  
  * ROLLUP/CUBE-Klausel hinzugefügt.  
  * Verbesserungen für NEXTVAL/CURVAL.  
  * Gruppieren von in SET-Klausel Spalten wurden Gruppierungssätze und Gruppieren von ID hinzugefügt.  
  * MERGE-Anweisung hinzugefügt.  
  * Unterstützung für die neue Datetime-Typen und Konvertierung von Datensätzen und Sammlungen als CLR-Datentypen hinzugefügt.  
* Ergänzt durch neue Funktionen der Tester. Tabellen jetzt getestet werden können als Objekte, die mit dem Testprogramm, eine Reihenfolge der Aufrufe gelistet mehrere getestet werden Objekte im Testfall kann geändert werden, Benutzer kann testen, Prozeduren und Funktionen mit Datensätzen und Sammlungen als Parameter und Rückgabewerte und ein Analyzer Abhängigkeiten wurde hinzugefügt, um zu überprüfen Nur verwendete Tabellen.  
  
## <a name="august-2007"></a>August 2007

Version August 2007 von SSMA für Oracle hinzugefügt:

* Eine neue Komponente der TESTER können Sie die zu erstellen, verwalten und Ausführen von Testfällen, um die konvertierten SQL-Code zu überprüfen.  
* Unterstützung für die Konvertierung von Oracle-Untertypen, Auflistungen und lokale Module an SQL-Konverter hinzugefügt wurde.  
* Ein neues Synchronisierungsfeature können Sie bestimmte Objekte mit SQL Server-Datenbank zu synchronisieren.  
* Neue Optionen.  
  
## <a name="april-2007"></a>April 2007

Von SSMA für Oracle Version April 2007 war die erste Version.
