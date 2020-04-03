---
title: Neuerungen in SSMA für SAP ASE (SybaseToSQL) | Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
ms.author: jtoland;alexiva
ms.openlocfilehash: 7f23c7e1c676b4ade42b43cf963e0fa6956f93c6
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625588"
---
# <a name="whats-new-in-ssma-for-sap-ase-sybasetosql"></a>Neuerungen in SSMA für SAP ASE (SybaseToSQL)

In diesem Artikel werden SQL Server Migration Assistant (SSMA) für SAP ASE -Änderungen (früher SSMA für Sybase) in jeder Version aufgeführt.

## <a name="ssma-v88"></a>SSMA v8.8

Die version8.8 version von SSMA für SAP ASE umfasst:

* Verbesserungen der SQL Server-Objektsynchronisierungsstabilität
* GUI-Leistungsverbesserungen bei Bewertung und Konvertierung
* Beheben des Problems mit fehlenden Zeichen in SQL-Definitionen für Objekte

## <a name="ssma-v87"></a>SSMA v8.7

Die version v8.7 von SSMA für SAP ASE enthält kleinere Korrekturen und Leistungsverbesserungen in der grafischen Benutzeroberfläche.

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v86"></a>SSMA v8.6

Zusätzlich zu einem gezielten Satz von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung wurde die version 8.6 von SSMA für SAP ASE durch eine Einstellung erweitert, die es Benutzern ermöglicht, erweiterte SSMA-Eigenschaften im konvertierten Code wegzulassen.

Um diese Einstellung zu nutzen, navigieren Sie in SSMA für SAP ASE zu Die > **allgemeine** > **Konvertierung**der > **Extras-Projekteinstellungen**, und aktualisieren Sie dann unter **Misc**den Wert der Einstellung **Erweiterte Eigenschaften auslassen** auf **Ja**. **Tools**

![Einstellung erweiterte Eigenschaften auslassen](../sybase/media/ssma-omit-extended-properties.png)

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v85"></a>SSMA v8.5

Die version8.5 von SSMA für SAP ASE wird durch Unterstützung für die Azure Active Directory-Authentifizierung und grundlegende Unterstützung für JSON-Funktionen in SQL-Servern sowie eine gezielte Reihe von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung erweitert.

Darüber hinaus können Sie mit SSMA für SAP ASE Systemtabellen und -ansichten jetzt ausblenden (sie von der Konvertierung ausschließen).

> [!IMPORTANT]
> Mit SSMA v8.5 ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v84"></a>SSMA v8.4

Die version8.4 von SSMA für SAP ASE wird um gezielte Korrekturen erweitert, die darauf ausgelegt sind, Barrierefreiheitsprobleme zu beheben und einen Fehler im Zusammenhang mit maximalen Indexspalten (um 32 statt 16 zu ermöglichen) für SQL Server 2016 und neuere Versionen zu beheben.

> [!IMPORTANT]
> Mit den SSMA-Versionen 7.4 bis 8.4 ist .NET 4.5.2 eine Installationsvoraussetzung.

## <a name="ssma-v83"></a>SSMA v8.3

Die version 8.3 von SSMA für SAP ASE wird um gezielte Korrekturen erweitert, die auf die Verbesserung von Qualitäts- und Konvertierungsmetriken ausgelegt sind. Darüber hinaus bietet diese Version von SSMA für SAP ASE Korrekturen, die:

* Beheben von Barrierefreiheitsproblemen
* Hinzufügen grundlegender `hierarchyid` Unterstützung für den Typ in SQL Server

## <a name="ssma-v82"></a>SSMA v8.2

Die version8.2 von SSMA für SAP ASE wird um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern sollen, sowie um Korrekturen für:

* Ein Problem mit deaktivierten nicht gruppierten Indizes nach der Datenmigration.
* Erkennung von .NET Framework während der stillen Installation.
* Ein gelegentlicher Absturz, der auftritt, wenn eine neue Version heruntergeladen wird.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.1 auf v8.2 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v81"></a>SSMA v8.1

Die version8.1 von SSMA für SAP ASE wird um gezielte Korrekturen erweitert, die auf die Verbesserung von Qualitäts- und Konvertierungsmetriken ausgelegt sind.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.0 auf v8.1 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v80"></a>SSMA v8.0

Die version v8.0 von SSMA für SAP ASE wird um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern sollen. Darüber hinaus bietet diese Version die folgenden neuen Funktionen:

* Unterstützung für **azure SQL Database Managed Instance** als Ziel. Sie können jetzt neue Projekte für Azure SQL Database Managed Instance erstellen:

  ![SQL DB MI-Projekt](../media/ssma-newproject-sqldbmi.png)

* Post-Conversion **Fix Advisor**. Erfahren Sie mehr darüber [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbank-/Schemaauswahl.

  Beim Herstellen einer Verbindung mit der Quelle kann der Benutzer nun Datenbanken/Schemas auswählen, die von Interesse sind. Wenn Sie nur die Schemas auswählen, die Sie migrieren möchten, sparen Sie Zeit während der ersten Verbindung und verbessern die Gesamtleistung von SSMA.

  ![SSMA-Filterobjekte](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

Die Version v7.10 von SSMA für SAP ASE wird um gezielte Korrekturen erweitert, die zusätzliche Sicherheits- und Datenschutzbestimmungen bieten, um Änderungen der globalen Anforderungen gerecht zu werden.

## <a name="ssma-v79"></a>SSMA v7.9

Die Version v7.9 von SSMA für SAP ASE enthält die folgenden Änderungen:

* Gezielte Korrekturen, die die Qualitäts- und Konvertierungsmetriken verbessern.
* Unterstützung in der SSMA-Befehlszeile zum Ändern der Datentypzuordnung und der Projekteinstellungen.
* Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach dem Konvertieren des Schemas ist es möglich, ein SSIS-Paket mithilfe einer Kontextmenüoption mit der rechten Maustaste zu erstellen.
* Das Dialogfeld für die Azure SQL-Datenbankverbindung in SSMA wurde ebenfalls geändert, um den vollqualifizierten Servernamen anzugeben. In früheren Versionen von SSMA musste das Präfix Azure SQL-Datenbank in den Projekteinstellungen explizit erwähnt werden.

## <a name="ssma-v78"></a>SSMA v7.8

Die Version v7.8 von SSMA für SAP ASE enthält die folgenden Änderungen:

* Änderungstypzuordnung, die in **den Projekteinstellungen**hervorgehoben ist.
* Die Möglichkeit für Benutzer, Telemetriedaten zu deaktivieren.

## <a name="ssma-v77"></a>SSMA v7.7

Die version 7.7-Version von SSMA für SAP ASE enthält die folgenden Änderungen:

* SSMA für SAP ASE wurde um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern.
* Basierend auf der beliebten Nachfrage ist die 32-Bit-Version von SSMA für SAP ASE zurück. Im Vergleich zur vorherigen Implementierung (vor version7.4) gibt es zwei Installationspakete, die jedoch nicht nebeneinander installiert werden können. Daher müssen Sie die am besten geeignete Version basierend auf den Konnektivitätskomponenten auswählen, die Sie haben. Es ist immer vorzuziehen, die 64-Bit-Version zu verwenden, wenn möglich.

## <a name="ssma-v76"></a>SSMA v7.6

Die Version v7.6 von SSMA für SAP ASE enthält die folgenden Änderungen:

* Gezielte Korrekturen zur Verbesserung der Qualitäts- und Konvertierungsmetriken und mit Unterstützung für SQL Server 2017 (öffentliche Vorschau). Die Unterstützung für SQL Server 2017 unter Windows und Linux befindet sich in der öffentlichen Vorschau und sollte nicht für Produktionsmigrationen verwendet werden.
* Unterstützung für die Konvertierung von Sybase-Funktionen.

## <a name="ssma-v75"></a>SSMA v7.5

Die version 7.5 von SSMA für SAP ASE (früher SSMA für Sybase) enthält die folgenden Änderungen:

* Mehrere Verbesserungen, um eine bessere Zugänglichkeit für Menschen mit Behinderungen zu gewährleisten.
* Unterstützung `CREATE OR REPLACE` für Syntax.

## <a name="ssma-v74"></a>SSMA v7.4

Die Version v7.4 von SSMA für Sybase enthält die folgenden Änderungen:

* Die **Option Abfragetimeout** ist jetzt während der Schemaobjektermittlung an Quelle und Ziel verfügbar.

  ![Abfragetimeoutoption](../media/query-timeout_red.png)
* Die Qualitäts- und Konvertierungsmetrik wurde durch gezielte Korrekturen auf Basis des Kundenfeedbacks verbessert.

  > [!IMPORTANT]
  > .NET 4.5.2 ist eine Voraussetzung für die Installation von SSMA v7.4. Darüber hinaus wird ab version7.4 die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v73"></a>SSMA v7.3

Die Version v7.3 von SSMA für Sybase enthält die folgenden Änderungen:

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

Die version 7.2 von SSMA für Sybase enthält die folgenden Änderungen:

* Verbesserte Qualitäts- und Konvertierungsmetrik mit gezielten Korrekturen basierend auf Kundenfeedback.
* Telemetrieverbesserungen, um bessere Datenpunkte bereitzustellen, um Kundenprobleme zu beheben und die Conversion-Raten von SSMA zu verbessern.

## <a name="ssma-v71"></a>SSMA v7.1

Die version 7.1 von SSMA für Sybase enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Diese Funktion befindet sich in der technischen Vorschau und unterstützt die Schema- und Datenverschiebung auf SQL-Clients.
* Unterstützung für automatische Updates, um die neueste Version von SSMA herunterzuladen, sobald es verfügbar ist.
* SSMA installierbare Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) bereitgestellt.

## <a name="may-2016"></a>Mai 2016

Die Version von SSMA für Sybase vom Mai 2016 enthält die folgenden Änderungen:

* Unterstützung für SQL Server 2016 wurde hinzugefügt.
* Installationsüberprüfung für .NET 2.0 entfernt.
* Die Extension Pack-Abhängigkeit wurde von .NET 3.5 auf .NET 4.0 aktualisiert.
* Behoben `save-project` `open-project` und Befehle für SSMA-Konsole.
* Fester `securepassword` Befehl für SSMA Console.
* Die Zählung der Objekte für die Erstbeladung wurde behoben.
* Fehler in globalen Einstellungen behoben.

## <a name="march-2016"></a>März 2016

Die Vorschauversion von SSMA für Sybase vom März 2016 bietet Unterstützung für die Migration zu SQL Server 2016.

## <a name="january-2016"></a>Januar 2016

Die Wartungsversion von SSMA für Sybase vom Januar 2016 enthält die folgenden Änderungen:

* Ansichtsprotokollmenüelement zu SSMA hinzugefügt (RFC 5706203).
* Telemetrie wurde hinzugefügt.

## <a name="july-2014"></a>Juli 2014

Die Version von SSMA für Sybase vom Juli 2014 enthält die folgenden Änderungen:

* Verbesserte Azure SQL DB-Codekonvertierung.
* Erweiterungspaketfunktionalität in Schema verschoben, um Azure SQL DB zu unterstützen.
* Es wurden Leistungsverbesserungen hinzugefügt, die für Datenbanken mit mehr als 10k-Objekten getestet wurden.
* UI-Verbesserungen für den Umgang mit einer großen Anzahl von Objekten hinzugefügt.
* Es wurde die Möglichkeit hinzugefügt, bekannte LOB-Schemas hervorzuheben (damit sie bei der Konvertierung ignoriert werden können).
* Verbesserung der Konvertierungsgeschwindigkeit wurde hinzugefügt.
* Es wurde die Möglichkeit hinzugefügt, Objektanzahlen in der Benutzeroberfläche anzuzeigen.
* Die Berichtsgröße wurde um mehr als 25 % reduziert.
* Verbesserte Fehlermeldungen für nicht analysierte Konstrukte.

## <a name="april-2014"></a>April 2014

Die Version von SSMA für Sybase vom April 2014 enthält die folgenden Änderungen:

* Unterstützung für MS SQL Server 2014 wurde hinzugefügt.
* Fehler bei der Konvertierung in Azure behoben.
* Fehler in Bezug auf unsichtbare Berichtsseiten in IE 10 behoben.

## <a name="january-2012"></a>Januar 2012

Die Version von SSMA für Sybase vom Januar 2012 enthält die folgenden Änderungen:

* Unterstützung für die Rollback-Triggerkonvertierung wurde hinzugefügt.
* Bereitgestellter Fix `@@ROWCOUNT` für `@@ERROR` die `SET` Konvertierung und in derselben Anweisung.

## <a name="july-2011"></a>Juli 2011

Die Version von SSMA für Sybase vom Juli 2011 bietet eine verbesserte Fehlerberichterstattung während der Datenmigration.

## <a name="april-2011"></a>Januar 2011

Die Version von SSMA für Sybase vom April 2011 enthält die folgenden Änderungen:

* Konsolidiertes Produkt "SSMA für Sybase", das [!INCLUDE [ssVersion2005](../../includes/ssversion2005-md.md)]unterstützt , [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)]und [!INCLUDE [ssSQL11](../../includes/ssSQL11-md.md)] Azure SQL.
* Unterstützung für das Verbinden und [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]Migrieren zu wurde hinzugefügt.
* Es wurde ein neues Feature zum Konvertieren und Migrieren von Sybase-Datenbanken in Azure SQL hinzugefügt.
* Verbessertes clientseitiges Datenmigrationsmodul, das die parallele Migration von Daten unterstützt.
* Verbesserte Datenmigrationsleistung mit einfachen und massenprotokollierten Wiederherstellungsmodellen.
* Es wurde die Möglichkeit hinzugefügt, Sybase-Datenbanken mit Groß-/Kleinschreibung ordnungsgemäß zu konvertieren und zu migrieren, um sql Server mit Groß-/Kleinschreibung zu berücksichtigen.
* Die Unterstützung für die Konvertierung von Sybase ASE Non-ANSI Join-Anweisungen in SQL Server ANSI join-Anweisungen wurde auf DELETE- und UPDATE-Anweisungen erweitert.
* Zusätzliche Konnektivitätsoptionen für die Verbindung mit Sybase ASE-Servern über den Sybase ASE ODBC-Anbieter und Sybase ASE ADO.NET-Anbietern bereitgestellt.
* Die Abhängigkeit von einer `SysDB`separaten Datenbank namens , die die Sybase-Emulationsfunktionen enthält (als Teil von Extension Pack installiert).
* Es wurde die Möglichkeit hinzugefügt, SSMA [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)] für Sybase Extension Pack auf Clustern zu installieren.
* Abwärtskompatibilität von Projekten hinzugefügt, die von früheren Versionen von SSMA (v4.0 und v4.2) erstellt wurden.
* Es wurde die Möglichkeit hinzugefügt, das SSMA für Sybase v5.0 Produkt Side-by-Side (SxS) mit älteren Versionen von SSMA (v4.0 und v4.2) zu installieren.

## <a name="july-2010"></a>Juli 2010

Die Version von SSMA für Sybase vom Juli 2010 fügte hinzu:

* Unterstützung für die Migration zu SQL Server 2008 R2.
* Eine neue SSMA-Konsolenanwendung für die Ausführung von Befehlszeilen.
* Unterstützung für die Datenmigration mit serverseitigen und clientseitigen Datenmigrationsmodulen.
* Unterstützung für die "Custom SELECT"-Anweisung bei der Datenmigration.
* Unterstützung für die Migration von Sybase ASE 15.0.3 und 15.5.

## <a name="june-2008"></a>Juni 2008

Die Version von SSMA für Sybase vom Juni 2008 enthält die folgenden Änderungen:

* SSMA Tester wurde hinzugefügt, der automatisch die Datenbankobjektkonvertierung und die von SSMA durchgeführte Datenmigration testet. Nachdem alle SSMA-Migrationsschritte abgeschlossen sind, verwenden Sie SSMA Tester, um zu überprüfen, ob konvertierte Objekte auf die gleiche Weise funktionieren und dass alle Daten ordnungsgemäß übertragen wurden.
* Pre-SQL-Konvertierung hinzugefügt. Der Benutzer kann nun temporäre Tabellendeklarationen (und andere Objektdeklarationen) für jede Quellprozedur angeben, die bei der Konvertierung verwendet werden soll.
* Verbesserungen bei der Objektkonvertierung hinzugefügt:
  * Die Verknüpfungskonvertierung wurde überarbeitet.
  * Aggregate und Nicht-Aggregate ohne Klauseln.
  * Die `IDENTITY` Funktion `SELECT INTO` mit einer Anweisung.
  * Gruppierte Einschränkungen und Indizes für Daten, die nur gesperrt sind.
  * Temporäre Tabellen, `SELECT INTO`die von erstellt wurden.
  * Einschränkungen / Indizes für temporäre Tabellen.
  * Neue [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)] Datetime-Typen werden unterstützt.
  * Unterstützung für Sybase 15.0-Konnektivität und Datentypen.

## <a name="may-2007"></a>Mai 2007

Die Version von SSMA für Sybase vom Mai 2007 fügte hinzu:

* Die Möglichkeit, Datenbankinhalte beim Speichern eines Projekts schneller zu laden.
* Unterstützung für vom Benutzer eingegebene Kommentare im SQL Server-formatierten SQL-Modus.
* Verbesserungen bei der Objektkonvertierung.

## <a name="november-2006"></a>Januar 2006

Die Version von SSMA für Sybase vom November 2006 enthält die folgenden Änderungen:

* Neue globale Einstellungen hinzugefügt:
  * Sie können Liniennummern in Editorfenstern anzeigen.
  * Sie können SSMA so konfigurieren, dass doppelte Objekte ersetzt werden oder duplikate Objekte während der Schemakonvertierung immer oder nie ersetzt werden.
* Es wurde eine neue Konvertierungsoption hinzugefügt, mit der Sie konfigurieren können, wie SSMA die folgenden Situationen behandelt:
  * Eine `CAST` `CONVERT` oder eine Anweisung, die eine Binärzeichenfolge enthält.
  * Überprüft NULL-Werte in Gleichheitsausdrücken.
  * Proxytabellen.
  * Fehlermeldungen der `RAISERROR`Benutzermeldung für .
  * `UPDATE`Anweisungen, die ungelöste Bezeichner enthalten.
* Es wurde eine neue Migrationsoption hinzugefügt, mit der Sie [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)] angeben können, wie SSMA Datumsangaben behandeln soll, die außerhalb des Datumsbereichs liegen.
* Auf der **SQL-Registerkarte** wurde eine **Formatierte SQL-Einstellung** hinzugefügt, die den Code für eine verbesserte Lesbarkeit formatiert.
* Fehlerbehebungen, einschließlich:
  * SSMA konvertiert `LOCK TABLE <table> IN { SHARED | EXCLUSIVE } MODE` nun Anweisungen, `TABLOCK` `TABLOCKX` indem sie `SELECT` der nachfolgenden Abfrage in der Tabelle einen oder einen Hinweis hinzufügt.
  * Die erforderlichen Umwandlungen werden nun hinzugefügt, wenn binäre Typen in Zeichenausdrücken verwendet werden.
  * Speicher- und Leistungsverbesserungen.

## <a name="july-2006"></a>Januar 2006

Die Version von Juli 2006 von SSMA für Sybase war die erste Version.

## <a name="see-also"></a>Siehe auch

[Erste Schritte mit SSMA für Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
