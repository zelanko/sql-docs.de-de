---
title: Neuerungen in SSMA für MySQL (MySQLToSql) | Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1451a0b0-6713-4d0c-954f-ea3d8fce1d31
ms.author: jtoland;alexiva
ms.openlocfilehash: 9d5c33bbb9e09a5a833c928547a5ec659fe43c96
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625553"
---
# <a name="whats-new-in-ssma-for-mysql-mysqltosql"></a>Neuerungen in SSMA für MySQL (MySqlToSql)

In diesem Artikel werden SQL Server Migration Assistant (SSMA) für MySQL-Änderungen in jeder Version aufgeführt.

## <a name="ssma-v88"></a>SSMA v8.8

Die version8.8 von SSMA für MySQL enthält:

* Verbesserungen der SQL Server-Objektsynchronisierungsstabilität
* GUI-Leistungsverbesserungen bei Bewertung und Konvertierung

## <a name="ssma-v87"></a>SSMA v8.7

Die version v8.7 von SSMA for MySQL hat kleinere Korrekturen und Leistungsverbesserungen in der grafischen Benutzeroberfläche.

Darüber hinaus bietet SSMA für MySQL jetzt Konvertierung für `LIMIT` Klauseln, wenn Sie auf Azure SQL abzielen.

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v86"></a>SSMA v8.6

Zusätzlich zu einem gezielten Satz von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung wurde die version 8.6 von SSMA for MySQL durch hinzufügen einer Einstellung verbessert, die es Benutzern ermöglicht, erweiterte SSMA-Eigenschaften im konvertierten Code wegzulassen.

Um diese Einstellung zu nutzen, navigieren Sie in SSMA für MySQL zu > **Extraprojekteinstellungen** > **allgemeine** > **Konvertierung**, und aktualisieren Sie dann unter **Misc**den Wert der Einstellung **Erweiterte Eigenschaften auslassen** auf **Ja**. **Tools**

![Einstellung erweiterte Eigenschaften auslassen](../mysql/media/ssma-omit-extended-properties.png)

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v85"></a>SSMA v8.5

Die version8.5 von SSMA for MySQL wird durch Unterstützung für die Azure Active Directory-Authentifizierung und grundlegende Unterstützung für JSON-Funktionen in SQL-Servern sowie eine gezielte Reihe von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung erweitert.

> [!IMPORTANT]
> Mit SSMA v8.5 ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v84"></a>SSMA v8.4

Die version8.4 von SSMA for MySQL wird um gezielte Korrekturen erweitert, die darauf ausgelegt sind, Barrierefreiheitsprobleme zu beheben und einen Fehler im Zusammenhang mit maximalen Indexspalten (um 32 statt 16 zu ermöglichen) für SQL Server 2016 und neuere Versionen zu beheben.

> [!IMPORTANT]
> Mit SSMA-Versionen 7.4, aber 8.4 ist .NET 4.5.2 eine Installationsvoraussetzung.

## <a name="ssma-v83"></a>SSMA v8.3

Die version 8.3 von SSMA for MySQL wird um gezielte Korrekturen erweitert, die zur Verbesserung der Qualität und der Konvertierungsmetriken entwickelt wurden. Darüber hinaus bietet diese Version von SSMA für MySQL Korrekturen, die:

* Beheben von Barrierefreiheitsproblemen.
* Fügen Sie `hierarchyid` grundlegende Unterstützung für den Typ in SQL Server hinzu.

## <a name="ssma-v82"></a>SSMA v8.2

Die version8.2 von SSMA for MySQL wird durch einen gezielten Satz von Korrekturen erweitert, die zur Verbesserung der Qualität und Konvertierungsmetriken sowie mit Korrekturen für:

* Ein Problem mit deaktivierten nicht gruppierten Indizes nach der Datenmigration.
* Erkennung von .NET Framework während der stillen Installation.
* Ein gelegentlicher Absturz, der auftritt, wenn eine neue Version heruntergeladen wird.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.1 auf v8.2 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v81"></a>SSMA v8.1

Die version8.1 von SSMA for MySQL wird um gezielte Korrekturen erweitert, die zur Verbesserung von Qualitäts- und Konvertierungsmetriken entwickelt wurden.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.0 auf v8.1 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v80"></a>SSMA v8.0

Die version8.0 von SSMA for MySQL wird um gezielte Korrekturen erweitert, die zur Verbesserung der Qualität und der Konvertierungsmetriken entwickelt wurden. Diese Version bietet auch die folgenden neuen Funktionen:

* Unterstützung für **azure SQL Database Managed Instance** als Ziel. Sie können jetzt neue Projekte für Azure SQL Database Managed Instance erstellen:

  ![SQL DB MI-Projekt](../media/ssma-newproject-sqldbmi.png)

* Post-Conversion **Fix Advisor**. Erfahren Sie mehr darüber [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbank-/Schemaauswahl.

  Beim Herstellen einer Verbindung mit der Quelle kann der Benutzer nun Datenbanken/Schemas auswählen, die von Interesse sind. Wenn Sie nur die Schemas auswählen, die Sie migrieren möchten, sparen Sie Zeit während der ersten Verbindung und verbessern die Gesamtleistung von SSMA.

  ![SSMA-Filterobjekte](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

Die Version v7.10 von SSMA für MySQL enthält die folgenden Änderungen:

* Gezielte Korrekturen, die zusätzliche Sicherheits- und Datenschutzbestimmungen bieten, um Änderungen der globalen Anforderungen gerecht zu werden.
* Ein Fix für die Konvertierung von Leerzeichen zwischen Funktionsname und Argumentliste.

## <a name="ssma-v79"></a>SSMA v7.9

Die version 7.9 von SSMA für MySQL enthält die folgenden Änderungen:

* Gezielte Korrekturen, die die Qualitäts- und Konvertierungsmetriken verbessern.
* Teilweise Unterstützung für die Migration räumlicher Datentypen von MySQL in Azure SQL-Datenbank.
* Unterstützung in der SSMA-Befehlszeile zum Ändern der Datentypzuordnung und der Projekteinstellungen.
* Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach dem Konvertieren des Schemas ist es möglich, ein SSIS-Paket mithilfe einer Kontextmenüoption mit der rechten Maustaste zu erstellen.
* Das Dialogfeld für die Azure SQL-Datenbankverbindung in SSMA wurde ebenfalls geändert, um den vollqualifizierten Servernamen anzugeben. In früheren Versionen von SSMA musste das Präfix Azure SQL-Datenbank in den Projekteinstellungen explizit erwähnt werden.

## <a name="ssma-v78"></a>SSMA v7.8

Die version 7.8 von SSMA für MySQL enthält die folgenden Änderungen:

* Änderungstypzuordnung, die in den Projekteinstellungen hervorgehoben ist.
* Die Möglichkeit für Benutzer, Telemetriedaten zu deaktivieren.

## <a name="ssma-v77"></a>SSMA v7.7

Die version 7.7 von SSMA für MySQL enthält die folgenden Änderungen:

* SSMA für MySQL wurde um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern.
* Basierend auf der beliebten Nachfrage ist die 32-Bit-Version von SSMA für MySQL zurück. Im Vergleich zur vorherigen Implementierung (vor version7.4) gibt es zwei Installationspakete, die jedoch nicht nebeneinander installiert werden können. Daher müssen Sie die am besten geeignete Version basierend auf den Konnektivitätskomponenten auswählen, die Sie haben. Es ist immer vorzuziehen, die 64-Bit-Version zu verwenden, wenn möglich.
* SSMA für MySQL verfügt jetzt über den ODBC Connection String-Verbindungsmodus, mit dem Sie alle ODBC-Treiber von Drittanbietern verwenden können, die mit MySQL kompatibel sind.

## <a name="ssma-v76"></a>SSMA v7.6

Die Version v7.6 von SSMA for MySQL wurde um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern, sowie um Unterstützung für SQL Server 2017 (öffentliche Vorschau). Die Unterstützung für SQL Server 2017 unter Windows und Linux befindet sich in der öffentlichen Vorschau und sollte nicht für Produktionsmigrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA v7.5

Die Version v7.5 von SSMA for MySQL wurde um einige Verbesserungen erweitert, um eine bessere Zugänglichkeit für Menschen mit Behinderungen zu gewährleisten.

## <a name="ssma-v74"></a>SSMA v7.4

Die version 7.4 von SSMA für MySQL enthält die folgenden Änderungen:

* Die **Option Abfragetimeout** ist jetzt während der Schemaobjektermittlung an Quelle und Ziel verfügbar.

    ![Abfragetimeoutoption](../media/query-timeout_red.png)
* Die Qualitäts- und Konvertierungsmetrik wurde durch gezielte Korrekturen auf Basis des Kundenfeedbacks verbessert.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung für die Installation von SSMA v7.4. Darüber hinaus wird ab version7.4 die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v73"></a>SSMA v7.3

Die Version v7.3 von SSMA für MySQL enthält die folgenden Änderungen:

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

Die version7.2 von SSMA for MySQL enthält die folgenden Änderungen:

* Verbesserte Qualitäts- und Konvertierungsmetrik mit gezielten Korrekturen basierend auf Kundenfeedback.
* Telemetrieverbesserungen, um bessere Datenpunkte bereitzustellen, um Kundenprobleme zu beheben und die Conversion-Raten von SSMA zu verbessern.

## <a name="ssma-v71"></a>SSMA v7.1

Die version7.1 von SSMA für MySQL enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Diese Funktion befindet sich in der technischen Vorschau und ermöglicht die Schema- und Datenverschiebung für SQL-Server.
* SSMA unterstützt jetzt automatische Updates, um die neueste Version von SSMA herunterzuladen, sobald es verfügbar ist.
* SSMA installierbare Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) bereitgestellt.

## <a name="may-2016"></a>Mai 2016

Die Version von SSMA for MySQL vom Mai 2016 enthält die folgenden Änderungen:

* Unterstützung für SQL Server 2016 wurde hinzugefügt.
* Verbesserter Parser und Resolver.
* Installationsüberprüfung für .NET 2.0 entfernt.
* Die Extension Pack-Abhängigkeit wurde von .NET 3.5 auf .NET 4.0 aktualisiert.
* Es wurde die standardmäßige BigInt-Typzuordnung für MySql behoben.
* Behoben `save-project` `open-project` und Befehle für SSMA-Konsole.
* Fester `securepassword` Befehl für SSMA Console.
* Die Zählung der Objekte für die Erstbeladung wurde behoben.
* Beim Laden von MsSql-Objekten wurde behoben.
* Fehler in globalen Einstellungen behoben.

## <a name="march-2016"></a>März 2016

Die Vorschauversion von SSMA für MySQL vom März 2016 bietet Unterstützung für die Migration zu SQL Server 2016.
  
## <a name="january-2016"></a>Januar 2016

Die Wartungsversion von SSMA for MySQL vom Januar 2016 enthält die folgenden Änderungen:

* Ansichtsprotokollmenüelement zu SSMA hinzugefügt (RFC 5706203).
* Telemetrie wurde hinzugefügt.
  
## <a name="july-2014"></a>Juli 2014

Die Version von SSMA for MySQL vom Juli 2014 enthält die folgenden Änderungen:
  
* Verbesserte Azure SQL DB-Codekonvertierung.
* Die Erweiterungspaketfunktionalität wurde in das Schema verschoben, um Azure SQL DB zu unterstützen.
* Leistungsverbesserungen wurden für Datenbanken mit über 10k-Objekten getestet.
* UI-Verbesserungen für den Umgang mit einer großen Anzahl von Objekten.
* Hervorhebung bekannter LOB-Schemas (damit sie bei der Konvertierung ignoriert werden können).
* Verbesserung der Konvertierungsgeschwindigkeit.
* Objektanzahl in der Benutzeroberfläche anzeigen.
* Größenreduzierung durch Bericht um mehr als 25 %.
* Verbesserte Fehlermeldungen für nicht analysierte Konstrukte.
  
## <a name="april-2014"></a>April 2014

Die Version von SSMA for MySQL vom April 2014 enthält die folgenden Änderungen:
  
* Unterstützung für SQL Server 2014 wurde hinzugefügt.
* Fehler bei der Konvertierung in Azure behoben.
* Fehler in Bezug auf unsichtbare Berichtsseiten in IE 10 behoben.
  
## <a name="july-2011"></a>Juli 2011

Die Version von SSMA for MySQL vom Juli 2011 enthält die folgenden Änderungen:
  
* Unterstützung für `LIMIT` die [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)] `OFFSET`Konvertierung von .
* Verbesserte Fehlerberichterstattung während der Datenmigration.
  
## <a name="april-2011"></a>Januar 2011

Die Version von SSMA for MySQL vom April 2011 enthält die folgenden Änderungen:
  
* Single installable of "SSMA for [!INCLUDE [ssVersion2005](../../includes/ssversion2005-md.md)]MySQL", das unterstützt , [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)]und [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)] Azure SQL.
* Die Möglichkeit, [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]eine Verbindung herzustellen.
* Verbessertes clientseitiges Datenmigrationsmodul, das die parallele Migration von Daten unterstützt.
* Verbesserte Datenmigrationsleistung mit einfachen und massenprotokollierten Wiederherstellungsmodellen.
* SSMA für MySQL Console-Version unterstützt Abwärtskompatibilität. Sie können die Projekte öffnen, die von Versionen zuvor in SSMA v5.0 erstellt wurden.
* SSMA für MySQL v5.0 Produkt kann nebeneinander (SxS) mit älteren Versionen von SSMA Produkt installiert werden.
  
## <a name="july-2010"></a>Juli 2010

Die Version von SSMA for MySQL vom Juli 2010 enthält die folgenden Funktionen:
  
**1. Verbesserungen an der Benutzeroberfläche:**

* Registerkarte 'SQL-Modi' für MySQL-Datenbankobjekte
* Registerkarte 'Einstellungen' für MySQL-Datenbankobjekte
* Registerkarte 'Daten' für MySQL-Tabellen
* Aktualisierte Projekteinstellungen auf Konvertierungs- und Migrationsseiten
* 'Datenmigrationseinstellungen' auf Tabellenebene
  
**2. Verbesserungen bei der Verbindung mit MySQL und SQL Server:**
  
* SSL-Konnektivität in MySQL
* Verschlüsselte Konnektivität in SQL Server
  
**3. Verbesserungen am MySQL Metabase Explorer:**
  
* Laden aller MySQL-Datenbankobjekte und ihrer jeweiligen Tabs.
  
**4. Verbesserungen bei der Objektkonvertierung:**
  
* Konvertierung von MySQL Metabase-Objekten - Prozeduren, Funktionen, Ansichten, Trigger und Anweisungen.
* Begrenzte Unterstützung für räumliche Datentypen in Tabellen.
* Option zum Konvertieren von MySQL-Funktionen in gespeicherte SQL Server-Prozeduren
* Option zum Anwenden von SQL-Modi und Charset-Zuordnung während der Objektkonvertierung
  
**5. Verbesserungen bei der Datenmigration:**  
  
* Unterstützung für die Datenmigration mit serverseitigen und clientseitigen Datenmigrationsmodulen
* Unterstützung für die Räumliche Datenmigration
* Benutzerdefinierte SQL für Datenmigration für Tabellen
  
**6. SSMA für MySQL-Konsole:**  
  
* Support Console-Funktion für SSMA für MySQL  
* Unterstützung für Script-Level Interfacing  
  
## <a name="january-2010"></a>Januar 2010

Die Version von SSMA für MySQL im Januar 2010 war die erste Version. Es enthielt die folgenden Merkmale:
  
* Unterstützung für die Migration sowohl zu lokalen SQL Server als auch zu Azure SQL hinzugefügt.  
  
* **Feature-Snapshot:** Schema- und Datenmigration von MySQL-Tabellen/Indizes/Einschränkungen.
