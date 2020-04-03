---
title: Neuerungen in SSMA für Oracle (OracleToSQL) | Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
ms.author: jtoland;alexiva
ms.openlocfilehash: 88b87aad931f28637accc95aa4d993037fcf0b0a
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625600"
---
# <a name="whats-new-in-ssma-for-oracle-oracletosql"></a>Neuerungen in SSMA für Oracle (OracleToSQL)

In diesem Artikel werden SQL Server Migration Assistant (SSMA) für Oracle-Änderungen in jeder Version aufgeführt.

## <a name="ssma-v88"></a>SSMA v8.8

Die version8.8 von SSMA für Oracle umfasst:

* Verbesserungen der SQL Server-Objektsynchronisierungsstabilität
* GUI-Leistungsverbesserungen bei Bewertung und Konvertierung
* Verbesserte Konvertierung `OVER PARTITION` von Analyseklauseln
* Neue Konvertierung `LEAD` für analytische Funktion
* Neue Konvertierung für Subquery-Faktoring-Klauseln
* Neue `REPLICATE` Verteilungsoption für Azure SQL Data Warehouse
* Brandneuer Oracle-Syntaxparser zur weiteren Verbesserung der Konvertierungsleistung

## <a name="ssma-v87"></a>SSMA v8.7

Die version version v8.7 von SSMA für Oracle enthält kleinere Korrekturen und Leistungsverbesserungen in der grafischen Benutzeroberfläche.

Darüber hinaus ermöglicht SSMA für Oracle jetzt das Filtern von Objekten basierend auf dem Gültigkeitsstatus im Dialogfeld "Erweiterte Objektauswahl".

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v86"></a>SSMA v8.6

Zusätzlich zu einem gezielten Satz von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung wurde die version 8.6 von SSMA für Oracle durch eine Einstellung erweitert, die es Benutzern ermöglicht, erweiterte SSMA-Eigenschaften im konvertierten Code wegzulassen.

Um diese Einstellung zu nutzen, navigieren Sie in SSMA für Oracle zu > **Extraprojekteinstellungen** > **allgemeine** > **Konvertierung**, und aktualisieren Sie dann unter **Misc**den Wert der Einstellung **Erweiterte Eigenschaften auslassen** auf **Ja**. **Tools**

![Einstellung erweiterte Eigenschaften auslassen](../oracle/media/ssma-omit-extended-properties.png)

Darüber hinaus bietet SSMA für Oracle jetzt `XMLTABLE` eine verbesserte Analyse der Klausel.

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v85"></a>SSMA v8.5

Die version8.5 von SSMA für Oracle wird durch Unterstützung für die Azure Active Directory-Authentifizierung und grundlegende Unterstützung für JSON-Funktionen in SQL-Servern sowie eine gezielte Reihe von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung erweitert.

Darüber hinaus wurde SSMA für Oracle um unterstützungsmittelergänzt:

* Beschränken der Anzahl ausgewählter Objekte für die Ermittlung `WHERE .. IN (..)` auf 990 (Oracles Klausellimit beträgt 1000 Elemente).
* Datenmigration `RAW` von `UNIQUEIDENTIFIER`nach .
* Parsing `PARALLEL_ENABLE` der Klausel.

Schließlich bietet die version8.5 von SSMA für Oracle nun Folgendes:

* Verbesserte Leistung konvertierter verpackter Konstanten.
* Ein Update für Oracle Data Provider für .NET auf Version 19.5.0.

> [!IMPORTANT]
> Mit SSMA v8.5 ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v84"></a>SSMA v8.4

Die Version v8.4 von SSMA für Oracle wird um gezielte Korrekturen erweitert, die darauf ausgelegt sind, Barrierefreiheitsprobleme zu beheben und einen Fehler im Zusammenhang mit maximalen Indexspalten (um 32 statt 16 zu ermöglichen) für SQL Server 2016 und neuere Versionen zu beheben.

Darüber hinaus fügt diese Version von SSMA für Oracle konvertierung `SYS_REFCURSOR` als gespeicherte Prozedurparameter `OUT` hinzu.

> [!IMPORTANT]
> Mit den SSMA-Versionen 7.4 bis 8.4 ist .NET 4.5.2 eine Installationsvoraussetzung.

## <a name="ssma-v83"></a>SSMA v8.3

Die version8.3 von SSMA für Oracle wird um gezielte Korrekturen erweitert, die auf die Verbesserung von Qualitäts- und Konvertierungsmetriken ausgelegt sind. Darüber hinaus bietet diese Version von SSMA für Oracle Korrekturen, die Folgendes bewirken:

* Beheben von Barrierefreiheitsproblemen.
* Fügen Sie `hierarchyid` grundlegende Unterstützung für den Typ in SQL Server hinzu.
* Beheben Sie ein Problem mit einem unbekannten Rückgabetyp für eine Funktion, die über Synonym aufgerufen wird.
* Aktualisieren sie ODP.NET auf v19.3.

## <a name="ssma-v82"></a>SSMA v8.2

Die version8.2 von SSMA für Oracle wurde erweitert um:

* Unterstützung für `DBMS_OUTPUT.ENABLE` / `DISABLE`hinzufügen.
* Entfernen `CAST AS FLOAT` `BINARY_FLOAT` für `BINARY_DOUBLE` und Spalten in der Standarddatenmigrationsabfrage.
* Fixsequenzen werden aktualisiert, wenn sich der aktuelle Wert geändert hat.
* Fehler beheben, der mit einer`ROWNUM`Fehlinterpretation von Pseudospalten ( usw.) zusammenhängt, wenn eine Spalte mit demselben Namen vorhanden ist.
* Beheben Eines Absturzes, `FOR` der beim Konvertieren von Schleifen mit mehrdeutigem ungelöstem Bezeichner auftritt.

Darüber hinaus enthält diese Version einen gezielten Satz von Korrekturen zur Verbesserung der Qualität und Konvertierungsmetriken sowie Korrekturen für:

* Ein Problem mit deaktivierten nicht gruppierten Indizes nach der Datenmigration.
* Erkennung von .NET Framework während der stillen Installation.
* Ein gelegentlicher Absturz, der auftritt, wenn eine neue Version heruntergeladen wird.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.1 auf v8.2 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v81"></a>SSMA v8.1

Die version8.1 von SSMA für Oracle wird um gezielte Korrekturen erweitert, die auf die Verbesserung von Qualitäts- und Konvertierungsmetriken ausgelegt sind.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.0 auf v8.1 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v80"></a>SSMA v8.0

Die version8.0 von SSMA für Oracle wird um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern sollen. Diese Version bietet auch die folgenden neuen Funktionen:

* Unterstützung für **azure SQL Database Managed Instance** als Ziel. Sie können jetzt neue Projekte für Azure SQL Database Managed Instance erstellen:

  ![SQL DB MI-Projekt](../media/ssma-newproject-sqldbmi.png)

  > [!NOTE]
  > Das SSMA für Oracle Extension Pack wurde ebenfalls aktualisiert, um Remoteinstallationen in Azure SQL Database Managed Instance zu ermöglichen:
  >
  > ![SSMA für Oracle Extension Pack](../media/ssma-oracle-ext-pack.png)

  Einige Features, einschließlich tester und serverseitig, werden nicht unterstützt, wenn sie auf die verwaltete Azure SQL-Datenbankinstanz abzielen. Weitere Informationen hierzu finden Sie [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/migrate-your-oracle-database-to-azure-sql-database-managed-instance-using-ssma-8-0/).

* Post-Conversion **Fix Advisor**. Erfahren Sie mehr darüber [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbank-/Schemaauswahl.

  Beim Herstellen einer Verbindung mit der Quelle kann der Benutzer nun Datenbanken/Schemas auswählen, die von Interesse sind. Wenn Sie nur die Schemas auswählen, die Sie migrieren möchten, sparen Sie Zeit während der ersten Verbindung und verbessern die Gesamtleistung von SSMA.

  ![SSMA-Filterobjekte](../media/ssma-filter-objects.png)

* Die Möglichkeit, den offiziellen, verwalteten .NET-Treiber zum Herstellen einer Verbindung mit Oracle zu verwenden. Der OCI-Treiber ist keine Voraussetzung mehr für die Verwendung des SQL Server-Migrationsassistenten für Oracle.

* Die Möglichkeit, `ROWID` `UROWID` standardmäßig `VARCHAR` zu zuordnen und zu. Geändert `uniqueidentifier` von, um die `ROWID` Datenmigration für explizite Spalten zu ermöglichen.

## <a name="ssma-v710"></a>SSMA v7.10

Die Version v7.10 von SSMA für Oracle enthält die folgenden Änderungen:

* Gezielte Korrekturen, die zusätzliche Sicherheits- und Datenschutzbestimmungen bieten, um Änderungen der globalen Anforderungen gerecht zu werden.
* Eine Konvertierungsverbesserung im Zusammenhang mit hierarchischen Abfragen.

## <a name="ssma-v79"></a>SSMA v7.9

Die Version v7.9 von SSMA für Oracle enthält die folgenden Änderungen:

* Gezielte Korrekturen, die die Qualitäts- und Konvertierungsmetriken verbessern.
* Unterstützung für die Migration von "Continue"-Anweisungen von Oracle zu SQL Server.
* Unterstützung in der SSMA-Befehlszeile zum Ändern der Datentypzuordnung und der Projekteinstellungen.
* Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach dem Konvertieren des Schemas ist es möglich, ein SSIS-Paket mithilfe einer Kontextmenüoption mit der rechten Maustaste zu erstellen.
* Das Dialogfeld für die Azure SQL-Datenbankverbindung in SSMA wurde ebenfalls geändert, um den vollqualifizierten Servernamen anzugeben. In früheren Versionen von SSMA musste das Präfix Azure SQL-Datenbank in den Projekteinstellungen explizit erwähnt werden.

## <a name="ssma-v78"></a>SSMA v7.8

Die Version v7.8 von SSMA für Oracle enthält die folgenden Änderungen:

* Unterstützung für:
  * Zeilenausdruck für `IN` die Klausel.
  * Implizite Typumwandlungen.
  * `UID`Konvertierung für Azure SQL-Datenbank.
* Änderungstypzuordnung, die in **den Projekteinstellungen**hervorgehoben ist.
* Die Möglichkeit für Benutzer, Telemetriedaten zu deaktivieren.

## <a name="ssma-v77"></a>SSMA v7.7

Die version 7.7 von SSMA für Oracle enthält die folgenden Änderungen:

* SSMA für Oracle wurde um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern.
* Basierend auf der beliebten Nachfrage ist die 32-Bit-Version von SSMA für Oracle zurück. Im Vergleich zur vorherigen Implementierung (vor version7.4) gibt es zwei Installationspakete, die jedoch nicht nebeneinander installiert werden können. Daher müssen Sie die am besten geeignete Version basierend auf den Konnektivitätskomponenten auswählen, die Sie haben. Es ist immer vorzuziehen, die 64-Bit-Version zu verwenden, wenn möglich.
* Die SQL Server 2017-Unterstützung ist jetzt offiziell mit dem Oracle Extension Pack, das auch unter Linux unterstützt wird (neue Remoteinstallationsoption). Beachten Sie, dass die Extension Pack-Funktionalität eingeschränkt ist, wenn sie unter Linux installiert ist, da die Funktionen für die Tester- und serverseitige Datenmigration nicht unterstützt werden.
* SSMA für Oracle ermöglicht es Ihnen, Materialisierte Ansichten als reguläre Tabellen zu migrieren (konfigurierbar durch die Einstellungen unter **Projekteinstellungen** -> **Synchronisierung** -> **entdecken Sie Backing Tables für materialisierte Ansichten**).

## <a name="ssma-v76"></a>SSMA v7.6

Die Version v7.6 von SSMA für Oracle wird um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern, sowie um Unterstützung für SQL Server 2017 (öffentliche Vorschau). Die Unterstützung für SQL Server 2017 unter Windows und Linux befindet sich in der öffentlichen Vorschau und sollte nicht für Produktionsmigrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA v7.5

Die version 7.5 von SSMA für Oracle enthält die folgenden Änderungen:

* Verbessert durch mehrere Verbesserungen, um eine bessere Zugänglichkeit für Menschen mit Behinderungen zu gewährleisten.
* Aktualisiert, um die Qualitäts- und Konvertierungsmetrik mit zielgerichteten Korrekturen zu verbessern, z. B. verbesserte Verarbeitung von Datums- und Float-Datentypen während der Datenmigration, basierend auf Kundenfeedback.

## <a name="ssma-v74"></a>SSMA v7.4

Die Version v7.4 von SSMA für Oracle enthält die folgenden Änderungen:

* SSMA für Oracle unterstützt jetzt Azure SQL Data Warehouse als Zielplattform für die Migration.

  ![Fenster „Neues Projekt“](../media/new-project.png)
  * Unterstützt die Data Warehouse-Speicheroptionen, wie in der folgenden Abbildung gezeigt:

  ![Speicheroptionen für Data Warehouse](../media/storage-options_red.png)
  * Unterstützt die Datenverteilungsoptionen, wie in der folgenden Abbildung dargestellt:

  ![Datenverteilung für Data Warehouse](../media/data-distribution_red.png)

* Die **Option Abfragetimeout** ist jetzt während der Schemaobjektermittlung an Quelle und Ziel verfügbar.

  ![Abfragetimeoutoption](../media/query-timeout_red.png)

* Die Qualitäts- und Konvertierungsmetrik wurde durch gezielte Korrekturen auf Basis des Kundenfeedbacks verbessert.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung für die Installation von SSMA v7.4. Darüber hinaus wird ab version7.4 die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v73"></a>SSMA v7.3

Die Version v7.3 von SSMA für Oracle enthält die folgenden Änderungen:

* Verbesserte Qualitäts- und Konvertierungsmetrik mit gezielten Korrekturen basierend auf Kundenfeedback.
* SSMA-Erweiterbarkeitsframework, das über die folgenden Elemente verfügbar gemacht wird:
  * Exportieren sie die Funktionalität in ein SQL Server Data Tools (SSDT)-Projekt.
    * Sie können jetzt Schemaskripts aus SSMA in ein SSDT-Projekt exportieren. Sie können die Schemaskripts verwenden, um zusätzliche Schemaänderungen vorzunehmen und die Datenbank bereitzustellen.

      ![Speichern als SSDT-Projektbefehl](../media/export-schema-scripts_red.png)
  * Bibliotheken, die von SSMA für die Durchführung benutzerdefinierter Konvertierungen verwendet werden können.
    * Sie können jetzt Code erstellen, der benutzerdefinierte Syntaxkonvertierungen und Konvertierungen verarbeiten kann, die zuvor nicht von SSMA verarbeitet wurden.
      * Anweisungen zum Erstellen eines benutzerdefinierten Konverters finden Sie in diesem [Blogbeitrag, Erweiterung der Konvertierungsfunktionen des SQL Server-Migrationsassistenten](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      * Laden Sie ein Beispielprojekt zur Konvertierung aus diesem [Blogbeitrag](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/)herunter.

## <a name="ssma-v72"></a>SSMA v7.2

Die version 7.2-Version von SSMA für Oracle enthält die folgenden Änderungen:

* Verbesserte Qualitäts- und Konvertierungsmetrik mit gezielten Korrekturen basierend auf Kundenfeedback.
* Telemetrieverbesserungen, um bessere Datenpunkte bereitzustellen, um Kundenprobleme zu beheben und die Conversion-Raten von SSMA zu verbessern.

## <a name="ssma-v71"></a>SSMA v7.1

Die version7.1-Version von SSMA für Oracle enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Diese Funktion befindet sich in der technischen Vorschau und ermöglicht die Schema- und Datenverschiebung für SQL-Server.
* SSMA unterstützt jetzt automatische Updates, um die neueste Version von SSMA herunterzuladen, sobald es verfügbar ist.
* SSMA installierbare Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) bereitgestellt.

## <a name="may-2016"></a>Mai 2016

Die Version von SSMA für Oracle vom Mai 2016 enthält die folgenden Änderungen:

* Unterstützung für SQL Server 2016 wurde hinzugefügt.
* Konvertierung von Oracle Flashback-Archivtabellen in SQL Server-Zeittabellen wurde hinzugefügt.

  > [!NOTE]
  > SSMA kopiert keine Verlaufsdaten aus Oracle Flashback Data Archive-Tabellen. Daher müssen die Verlaufsdaten während des Migrationsprozesses manuell kopiert werden. Darüber hinaus zeigt SSMA die Verlaufstabelle im SQL Server-Metadaten-Explorer nicht an, da sie als Systemtabelle behandelt wird, aber Sie können die Verlaufstabelle in SQL Server Management Studio anzeigen.
  >
  > SQL Server 2016 unterstützt nicht mehrere Oracle Flashback-Funktionen, darunter:
  >
  >   * Oracle Flashback-Transaktionsabfrage
  >   * `DBMS_FLASHBACK`Paket
  >   * Flashback-Transaktion
  >   * Flashback-Datenarchiv
  >   * Rückblendentabelle
  >   * Rückblende Drop
  >   * Flashback-Datenbank

* Konvertierung von Oracle VPD-Richtlinien in SQL Server-Richtlinienobjekte hinzugefügt (Row Level Security for Oracle).
* Verringerte Zeit des ersten Ladens für Oracle.
* Verbesserter Parser und Resolver.
* Installationsüberprüfung für .NET 2.0 entfernt.
* Die Extension Pack-Abhängigkeit wurde von .NET 3.5 auf .NET 4.0 aktualisiert.
* Behoben `save-project` `open-project` und Befehle für SSMA-Konsole.
* Fester `securepassword` Befehl für SSMA Console.
* Die Zählung der Objekte für die Erstbeladung wurde behoben.
* Die Konvertierung von Zeichendatentypen für Oracle wurde behoben.
* Fehler in den globalen Einstellungen behoben.

## <a name="march-2016"></a>März 2016

Die Vorschauversion von SSMA für Oracle vom März 2016 hat Unterstützung für folgende Themen hinzugefügt:

* Migration zu SQL Server 2016.
* Migration der Oracle Row Level Security (mit einigen Einschränkungen).
* Migration von Oracle in Speichertabellen in den SQL Server Column Store.

## <a name="january-2016"></a>Januar 2016

Die Wartungsversion von SSMA für Oracle vom Januar 2014 enthält die folgenden Änderungen:

* Unterstützung für Clustered Indexes wurde hinzugefügt.
* Langsame Oracle-Schemaabfragen behoben (RFC 5076207).
* Es wurde eine Verbindung mit Azure über die Konsole hergestellt.
* Ansichtsprotokollmenüelement zu SSMA hinzugefügt (RFC 5706203).
* Telemetrie wurde hinzugefügt.

## <a name="july-2014"></a>Juli 2014

Die Version von SSMA für Oracle vom Juli 2014 enthält die folgenden Änderungen:

* Unterstützung für Azure SQL DB wurde hinzugefügt.
* Die Erweiterungspaketfunktionalität wurde in das Schema verschoben, um Azure SQL DB zu unterstützen.
* Unterstützung für Oracle Materialized Views wurde hinzugefügt.
* Unterstützung für SQL Server 2014 Memory-optimierte Tabellen wurde hinzugefügt.
* Enthaltene Leistungsverbesserungen, die für Datenbanken mit mehr als 10k-Objekten getestet wurden.
* UI-Verbesserungen für den Umgang mit einer großen Anzahl von Objekten hinzugefügt.
* Hervorhebung bekannter LOB-Schemas hinzugefügt.
* Inklusive Conversion-Geschwindigkeitsverbesserungen.
* Unterstützung für die Anzeige von Objektanzahlen in der Benutzeroberfläche wurde hinzugefügt.
* Die Berichtsgröße wurde um mehr als 25 % reduziert.
* Verbesserte Fehlermeldungen für nicht analysierte Konstrukte.

## <a name="april-2014"></a>April 2014

Die Version von SSMA für Oracle vom April 2014 enthält die folgenden Änderungen:

* Unterstützung für MS SQL Server 2014 wurde hinzugefügt.
* Unterstützung für Oracle 12 und Abfrageoptimierung hinzugefügt.
* Fehler bei der Konvertierung in Azure behoben.
* Fehler in Bezug auf unsichtbare Berichtsseiten in IE 10 behoben.

## <a name="january-2012"></a>Januar 2012

Die Version von SSMA für Oracle vom `RowType` Januar `RecordType` 2012 `NULL`bietet Unterstützung für und Eingabeparameter, die standardmäßig auf .

## <a name="july-2011"></a>Juli 2011

Die Version von SSMA für Oracle vom Juli 2011 enthält die folgenden Änderungen:

* Unterstützung für die Konvertierung [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)] des Oracle-Sequenz-zu-Sequenzgenerators wurde hinzugefügt.
* Verbesserte Fehlerberichterstattung während der Datenmigration.
* Verbesserte Konvertierung der Anweisung mit reservierten Wörtern.
* Verbesserte implizite Konvertierung des Datumswerts in einer Funktion.

## <a name="april-2011"></a>Januar 2011

Die Version von SSMA für Oracle vom April 2011 enthält die folgenden Änderungen:

* Konsolidiertes "SSMA für Oracle"-Produkt, das [!INCLUDE [ssVersion2005](../../includes/ssversion2005-md.md)]unterstützt, [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)] und [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)].
* Unterstützung für das Verbinden und [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]Migrieren zu wurde hinzugefügt.
* Verbessertes clientseitiges Datenmigrationsmodul, das die parallele Migration von Daten unterstützt.
* Verbesserte Datenmigrationsleistung `Simple` `Bulk` mit und protokollierten Wiederherstellungsmodellen.
* Unterstützung für die Abwärtskompatibilität von Projekten, die von früheren Versionen von SSMA (v4.0 und v4.2) erstellt wurden, wurde hinzugefügt.
* Es wurde die Möglichkeit hinzugefügt, SSMA für Oracle v5.0 Produkt nebeneinander (SxS) mit älteren Versionen von SSMA (v4.0 und v4.2) zu installieren.
* Unterstützung für die Meldung von benutzerdefinierten `VARRAY`Typen `NESTED TABLE`(einschließlich Subtype, , , Objekttabelle und Objektansicht) und deren Verwendungen in PL/SQL-Blöcken mit speziellen Fehlermeldungen wurde hinzugefügt.

## <a name="july-2010"></a>Juli 2010

Die Version von SSMA für Oracle vom Juli 2010 fügte hinzu:

* Unterstützung für die Migration zu SQL Server 2008 R2.
* Eine neue SSMA-Konsolenanwendung für die Ausführung von Befehlszeilen.
* Unterstützung für die Datenmigration mit serverseitigen und clientseitigen Datenmigrationsmodulen.
* Unterstützung für die "Custom SELECT"-Anweisung bei der Datenmigration.
* Unterstützung für die Migration von Oracle 11g R2.

## <a name="june-2008"></a>Juni 2008

Die Version von SSMA für Oracle vom Juni 2008 enthält die folgenden Änderungen:

* Verbesserungen am Bewertungsbericht hinzugefügt, einschließlich zusätzlicher Informationen für Synonyme, Rohquelle für parsierbare Objekte, Panels und sql Server-Logo-Entfernung sowie Layoutpersistenz.
* Verbesserungen bei der Objektkonvertierung hinzugefügt:
  * Pakete `DBMS_LOB` `DBMS_SQL` , Konvertierung hinzugefügt.
  * Die Verknüpfungskonvertierung wurde überarbeitet.
  * Änderung der Sammlungen und Datensatzkonvertierung, jetzt Konvertierung von Datensätzen in einfachen Fällen über separate Variablen für jedes Feld freigegeben.
  * Verbesserungen der Datensatz- und Sammlungsimplementierung.
  * Fensteraggregationsfunktionen hinzugefügt.
  * `ROLLUP`/`CUBE`Klausel hinzugefügt.
  * Verbesserung `NEXTVAL` / `CURVAL`für .
  * Spaltengruppierung in `SET` Klausel, Gruppierungssätze und Gruppierungs-ID wurden hinzugefügt.
  * `MERGE`Anweisung hinzugefügt.
  * Unterstützung neuer Datumszeittypen und Konvertierung von Datensätzen und Sammlungen als hinzugefügte CLR-Datentypen.
* Neue Funktionen von Tester hinzugefügt. Tabellen können jetzt als Objekte mit Tester getestet werden, eine Aufrufreihenfolge mehrerer testbarer Objekte im Testfall kann geändert werden, Benutzer können Prozeduren und Funktionen mit Datensätzen und Auflistungen als Parameter und Rückgabewerte testen, und es wurde ein Abhängigkeitsanalysator hinzugefügt, um nur verwendete Tabellen zu überprüfen.
  
## <a name="august-2007"></a>Januar 2007

Die Version von SSMA für Oracle vom August 2007 fügte hinzu:

* Mit einer neuen Tester-Komponente können Sie Testfälle erstellen, verwalten und ausführen, um konvertierten SQL-Code zu überprüfen.
* Unterstützung für die Konvertierung von Oracle-Subtypes, Sammlungen und lokalen Modulen wurde dem SQL-Konverter hinzugefügt.
* Mit einer neuen Synchronisierungsfunktion können Sie bestimmte Objekte mit der SQL Server-Datenbank synchronisieren.
* Neue Konvertierungsoptionen.
  
## <a name="april-2007"></a>Januar 2007

Die Veröffentlichung von SSMA für Oracle im April 2007 war die erste Veröffentlichung.
