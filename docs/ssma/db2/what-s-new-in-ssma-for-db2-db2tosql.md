---
title: Neuerungen in SSMA für DB2 (DB2ToSQL) | Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1cc38f85-3caa-42d0-8c76-a380c1d15c67
ms.author: jtoland;alexiva
ms.openlocfilehash: 53a159627750a5ec66b5aa0b3fd6510c647e26a5
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625525"
---
# <a name="whats-new-in-ssma-for-db2-db2tosql"></a>Neuerungen in SSMA für DB2 (DB2ToSQL)

In diesem Artikel werden SQL Server Migration Assistant (SSMA) für DB2-Änderungen in jeder Version aufgeführt.

## <a name="ssma-v88"></a>SSMA v8.8

Die version8.8 von SSMA für DB2 enthält:

* Verbesserungen der SQL Server-Objektsynchronisierungsstabilität
* GUI-Leistungsverbesserungen bei Bewertung und Konvertierung
* Aktualisierte `ROWID` Zuordnung `varbinary(40)` von zu zur Erleichterung der Datenmigration
* Verbesserte Konvertierung `SELECT ... FROM NEW/OLD TABLE` von Anweisungen
* Neukonvertierung `ALTER` von Anweisungen für Prozeduren und Funktionen
* Neukonvertierung von Zerstörungsaufträgen

## <a name="ssma-v87"></a>SSMA v8.7

Die version v8.7 von SSMA für DB2 enthält einen brandneuen DB2-Syntaxparser sowie kleinere Korrekturen und Leistungsverbesserungen in der grafischen Benutzeroberfläche.

Darüber hinaus bietet SSMA für DB2 jetzt:

* Eine Lösung für die Erkennung von Fremdschlüsseln bei der Migration von DB2 auf LUW.
* Verbesserte Konvertierung `SELECT ... FOR UPDATE` der Anweisung.
* Verbesserte Konvertierung `COUNT` für Funktion in MQ-Tabellen.
* Konvertierung `SAVEPOINT` von Anweisungen.
* Konvertierung, um das Verhalten `NULL` von `ORDER BY` DB2 für Werte in Klausel zu emulieren.
* Analyseunterstützung für ASSOCIATE RESULT SET-Anweisung.

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v86"></a>SSMA v8.6

Zusätzlich zu einem gezielten Satz von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung wurde die version 8.6 von SSMA für DB2 durch hinzufügen einer Einstellung verbessert, die es Benutzern ermöglicht, erweiterte SSMA-Eigenschaften im konvertierten Code wegzulassen.

Um diese Einstellung zu nutzen, navigieren Sie in SSMA für DB2 zu > **Extraprojekteinstellungen** > **allgemeine** > **Konvertierung**, und aktualisieren Sie dann unter **Misc**den Wert der Einstellung **Erweiterte Eigenschaften auslassen** auf **Ja**. **Tools**

![Einstellung erweiterte Eigenschaften auslassen](../db2/media/ssma-omit-extended-properties.png)

Darüber hinaus bietet SSMA für DB2 jetzt:

* Eine Korrektur für die Konvertierung von Funktionen, die Standardargumentwerte verwenden.
* Verbesserte Analyse der `PARAMETER` Klausel für Funktionen.
* Die Möglichkeit, `LEAVE` die Anweisung zu konvertieren.

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v85"></a>SSMA v8.5

Die version8.5 von SSMA für DB2 wird durch Unterstützung für die Azure Active Directory-Authentifizierung und grundlegende Unterstützung für JSON-Features in SQL-Servern sowie eine gezielte Reihe von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung erweitert.

Darüber hinaus wurde SSMA für DB2 um:

* Unterstützung für das `GET DIAGNOSTICS` Hinzufügen `ROW_NUMBER`der Konvertierung für Anweisung mit .
* Eine Korrektur für einen Fehler im Zusammenhang mit Leerzeichen am Anfang des Objektnamens, der nicht eingehalten wird.

> [!IMPORTANT]
> Mit SSMA v8.5 ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v84"></a>SSMA v8.4

Die Version v8.4 von SSMA für DB2 wird um gezielte Korrekturen erweitert, die darauf ausgelegt sind, Barrierefreiheitsprobleme zu beheben und einen Fehler im Zusammenhang mit maximalen Indexspalten (um 32 statt 16 zu ermöglichen) für SQL Server 2016 und neuere Versionen zu beheben.

> [!IMPORTANT]
> Mit SSMA-Versionen 7.4, aber 8.4 ist .NET 4.5.2 eine Installationsvoraussetzung.

## <a name="ssma-v83"></a>SSMA v8.3

Die Version v8.3 von SSMA für DB2 wird um gezielte Korrekturen erweitert, die zur Verbesserung der Qualität und der Konvertierungsmetriken entwickelt wurden. Darüber hinaus bietet diese Version von SSMA für DB2 Korrekturen, die Folgendes:

* Beheben von Barrierefreiheitsproblemen.
* Fügen Sie `hierarchyid` grundlegende Unterstützung für den Typ in SQL Server hinzu.
* Ersetzen Sie die TRIM-Funktionsverwendung `RTRIM` / `LTRIM`in z/OS-Erkennungsabfragen durch .
* Erlauben Sie dem Benutzer, Package Collection anzugeben, wenn `NULLID`eine Verbindung im 'Standardmodus' hergestellt wird (Standardeinstellung für ).
* Konvertierung für `CREATE TABLE AS SELECT`hinzufügen.
* Verbessern Sie Konvertierungen für globale temporäre Tabellen.
* Beheben Sie ein Problem mit der Überprüfungsreihenfolge der Objekteindeutigkeit, um Tabellen über Einschränkungen zu priorisieren, wenn Namen kollidieren.
* Beheben Sie ein Problem mit `DATE` dem `TIMESTAMP` Laden von Standardspaltenwerten für und für z/OS.
* Unterstützung Unicode-Zeilenvorschubzeichen `NEL`(auch bekannt als ).
* Beheben Eines Problems mit `RETURN TO` der Cursorkonvertierung mit fehlender Klausel.
* Hinzufügen von Unterstützung `GOTO`für Beschriftungen und .

## <a name="ssma-v82"></a>SSMA v8.2

Die version8.2-Version von SSMA für DB2 wurde erweitert, um Probleme mit Verbindungen mit Azure SQL-Datenbank über das SSMA-Konsolentool zu beheben und COUNT_BIG Spalte in der Ansichtsdeklaration während der Konvertierung zu vermissen. Darüber hinaus enthält diese Version einen gezielten Satz von Korrekturen zur Verbesserung der Qualität und Konvertierungsmetriken sowie Korrekturen für:

* Ein Problem mit deaktivierten nicht gruppierten Indizes nach der Datenmigration.
* Erkennung von .NET Framework während der stillen Installation.
* Ein gelegentlicher Absturz, der auftritt, wenn eine neue Version heruntergeladen wird.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.1 auf v8.2 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v81"></a>SSMA v8.1

Die Version v8.1 von SSMA für DB2 wurde erweitert, um gezielte Korrekturen bereitzustellen, die zur Verbesserung von Qualitäts- und Konvertierungsmetriken entwickelt wurden.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.0 auf v8.1 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v80"></a>SSMA v8.0

Die versionversion v8.0 von SSMA für DB2 wurde erweitert, um gezielte Korrekturen zur Verbesserung von Qualitäts- und Konvertierungsmetriken bereitzustellen. Diese Version bietet auch die folgenden neuen Funktionen:

* Unterstützung für **azure SQL Database Managed Instance** als Ziel. Sie können jetzt neue Projekte für Azure SQL Database Managed Instance erstellen:

  ![SQL DB MI-Projekt](../media/ssma-newproject-sqldbmi.png)

* Post-Conversion **Fix Advisor**. Erfahren Sie mehr darüber [hier](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Vorläufige Datenbank-/Schemaauswahl.

  Beim Herstellen einer Verbindung mit der Quelle kann der Benutzer nun Datenbanken/Schemas auswählen, die von Interesse sind. Wenn Sie nur die Schemas auswählen, die Sie migrieren möchten, sparen Sie Zeit während der ersten Verbindung und verbessern die Gesamtleistung von SSMA.

  ![SSMA-Filterobjekte](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

Die Version v7.10 von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Korrekturen, die zusätzliche Sicherheits- und Datenschutzbestimmungen bieten, um Änderungen der globalen Anforderungen gerecht zu werden.
* Ein Fix für `BEGIN-END` die Konvertierung von Blöcken.

## <a name="ssma-v79"></a>SSMA v7.9

Die Version v7.9 von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Korrekturen, die die Qualitäts- und Konvertierungsmetriken verbessern.
* Unterstützung in der SSMA-Befehlszeile zum Ändern der Datentypzuordnung und der Projekteinstellungen.
* Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach dem Konvertieren des Schemas ist es möglich, ein SSIS-Paket mithilfe einer Kontextmenüoption mit der rechten Maustaste zu erstellen.
* Das Dialogfeld für die Azure SQL-Datenbankverbindung in SSMA wurde ebenfalls geändert, um den vollqualifizierten Servernamen anzugeben. In früheren Versionen von SSMA musste das Präfix Azure SQL-Datenbank in den Projekteinstellungen explizit erwähnt werden.

## <a name="ssma-v78"></a>SSMA v7.8

Die Version v7.8 von SSMA für DB2 enthält die folgenden Änderungen:

* Änderungstypzuordnung, die in *den Projekteinstellungen*hervorgehoben ist.
* Die Möglichkeit für Benutzer, Telemetriedaten zu deaktivieren.

## <a name="ssma-v77"></a>SSMA v7.7

Die Version v7.7 von SSMA für DB2 enthält die folgenden Änderungen:

* Gezielte Korrekturen, die die Qualitäts- und Konvertierungsmetriken verbessern.
* Basierend auf der beliebten Nachfrage ist die 32-Bit-Version von SSMA für DB2 zurück. Im Vergleich zur vorherigen Implementierung (vor version7.4) gibt es zwei Installationspakete, die jedoch nicht nebeneinander installiert werden können. Daher müssen Sie die am besten geeignete Version basierend auf den Konnektivitätskomponenten auswählen, die Sie haben. Es ist immer vorzuziehen, die 64-Bit-Version zu verwenden, wenn möglich.

## <a name="ssma-v76"></a>SSMA v7.6

Die Version v7.6 von SSMA für DB2 wird um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern, sowie um Unterstützung für SQL Server 2017 (öffentliche Vorschau). Die Unterstützung für SQL Server 2017 unter Windows und Linux befindet sich in der öffentlichen Vorschau und sollte nicht für Produktionsmigrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA v7.5

Die Version v7.5 von SSMA für DB2 wurde um mehrere Verbesserungen erweitert, um eine bessere Zugänglichkeit für Menschen mit Behinderungen zu gewährleisten.

## <a name="ssma-v74"></a>SSMA v7.4

Die Version v7.4 von SSMA für DB2 enthält die folgenden Änderungen:

* Die **Option Abfragetimeout** ist jetzt während der Schemaobjektermittlung an Quelle und Ziel verfügbar.

  ![Abfragetimeoutoption](../media/query-timeout_red.png)

* Die Qualitäts- und Konvertierungsmetrik wurde durch gezielte Korrekturen auf Basis des Kundenfeedbacks verbessert.

  > [!IMPORTANT]
  > .NET 4.5.2 ist eine Voraussetzung für die Installation von SSMA v7.4. Darüber hinaus wurde ab version7.4 die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v73"></a>SSMA v7.3

Die Version v7.3 von SSMA für DB2 enthält die folgenden Änderungen:

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

Die Version v7.2 von SSMA für DB2 enthält die folgenden Änderungen:

* Verbesserte Qualitäts- und Konvertierungsmetrik mit gezielten Korrekturen basierend auf Kundenfeedback.
* Telemetrieverbesserungen, um bessere Datenpunkte bereitzustellen, um Kundenprobleme zu beheben und die Conversion-Raten von SSMA zu verbessern.

## <a name="ssma-v71"></a>SSMA v7.1

Die Version v7.1 von SSMA für DB2 enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Diese Funktion befindet sich in der technischen Vorschau und ermöglicht die Schema- und Datenverschiebung für SQL-Server.
* Unterstützung für automatische Updates, um die neueste Version von SSMA herunterzuladen, sobald es verfügbar ist.
* SSMA installierbare Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) bereitgestellt.

## <a name="may-2016"></a>Mai 2016

Die Version von SSMA für DB2 vom Mai 2016 enthält die folgenden Änderungen:

* Unterstützung für SQL Server 2016 wurde hinzugefügt.
* Konvertierung von DB2-In-Memory- und Stammtischen in SQL Server-In-Memory- und Hekaton-Features hinzugefügt.
* Konvertierung von DB2-Zugriffssteuerungen in SQL Server-Richtlinienobjekte hinzugefügt (Row Level Security for DB2).
* Konvertierung von DB2-Tabellen mit Systemversion in SQL Server-Zeittabellen hinzugefügt.
* Verbesserter DB2-Parser und Resolver.
* Installationsüberprüfung für .NET 2.0 entfernt.
* Unnötige \*.dll aus db2 Installer entfernt.
* Behoben `save-project` `open-project` und Befehle für SSMA-Konsole.
* Fester `securepassword` Befehl für SSMA Console.
* Die Zählung der Objekte für die Erstbeladung wurde behoben.
* Fehler in globalen Einstellungen behoben.
  
## <a name="march-2016"></a>März 2016

Die Vorschauversion von SSMA für DB2 vom März 2016 bietet Unterstützung für die Migration zu SQL Server 2016.

## <a name="january-2016"></a>Januar 2016

Die Wartungsversion von SSMA für DB2 vom Januar 2016 enthält die folgenden Änderungen:
  
* Unterstützung für eine Reihe von Standardfunktionen hinzugefügt.
* Db2-Parserfehler behoben.
* Behobene DB2 v9 zOS-Unterstützung (RFC 5690920).
* Fehler bei db2 wurden während der Konvertierung behoben.
* Ansichtsprotokollmenüelement zu SSMA hinzugefügt (RFC 5706203).
* Telemetrie wurde hinzugefügt.
  
## <a name="november-2014"></a>November 2014

Die Veröffentlichung von SSMA für DB2 im November 2014 war die erste Version.
