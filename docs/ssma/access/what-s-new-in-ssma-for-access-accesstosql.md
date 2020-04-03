---
title: Neuerungen in SSMA for Access (AccessToSQL) | Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: a24d3fc0-6911-4bfa-828a-197abf222e02
ms.author: jtoland;alexiva
ms.openlocfilehash: 2fd3da31e6a635a65f3d2a2f75320dd0586159d9
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625580"
---
# <a name="whats-new-in-ssma-for-access-accesstosql"></a>Neuerungen in SSMA for Access (AccessToSQL)

In diesem Artikel werden SQL Server Migration Assistant (SSMA) für Zugriffsänderungen in jeder Version aufgeführt.

## <a name="ssma-v88"></a>SSMA v8.8

Die version8.8 von SSMA for Access enthält:

* Verbesserungen der SQL Server-Objektsynchronisierungsstabilität
* GUI-Leistungsverbesserungen bei Bewertung und Konvertierung
* Brandneuer Access-Syntaxparser zur weiteren Verbesserung der Konvertierungsleistung

## <a name="ssma-v87"></a>SSMA v8.7

Die version v8.7 von SSMA for `IIF` Access hat die Konvertierung für die Funktion in Abfragen sowie kleinere Korrekturen und Leistungsverbesserungen in der grafischen Benutzeroberfläche verbessert.

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v86"></a>SSMA v8.6

Zusätzlich zu einem gezielten Satz von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung wurde die version 8.6 von SSMA for Access durch hinzufügeneiner Einstellung erweitert, die es Benutzern ermöglicht, erweiterte SSMA-Eigenschaften im konvertierten Code wegzulassen.

Um diese Einstellung zu nutzen, navigieren Sie in SSMA for Access zu > **Extraprojekteinstellungen** > **allgemeine** > **Konvertierung**, und aktualisieren Sie dann unter **Misc**den Wert der Einstellung **Erweiterte Eigenschaften auslassen** auf **Ja**. **Tools**

![Einstellung erweiterte Eigenschaften auslassen](../access/media/ssma-omit-extended-properties.png)

> [!IMPORTANT]
> Mit SSMA v8.5 und höher ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v85"></a>SSMA v8.5

Die version8.5 von SSMA for Access wird durch Unterstützung für die Azure Active Directory-Authentifizierung und grundlegende Unterstützung für JSON-Funktionen in SQL-Servern sowie eine gezielte Reihe von Korrekturen zur Verbesserung der Benutzerfreundlichkeit und Leistung erweitert.

Darüber hinaus unterstützt SSMA for Access jetzt`ISNULL`die `IIF`Konvertierung mehrerer Standardfunktionen ( , , usw.).

> [!IMPORTANT]
> Mit SSMA v8.5 ist .NET 4.7.2 eine Installationsvoraussetzung. Wenn Sie diese Version installieren müssen, können Sie die Laufzeitdatei von [hier](https://dotnet.microsoft.com/download/dotnet-framework/net472)herunterladen.

## <a name="ssma-v84"></a>SSMA v8.4

Die Version v8.4 von SSMA for Access wird um gezielte Korrekturen erweitert, die darauf ausgelegt sind, Barrierefreiheitsprobleme zu beheben und einen Fehler im Zusammenhang mit maximalen Indexspalten (um 32 statt 16 zu ermöglichen) für SQL Server 2016 und neuere Versionen zu beheben.

> [!IMPORTANT]
> Mit SSMA-Versionen 7.4, aber 8.4 ist .NET 4.5.2 eine Installationsvoraussetzung.

## <a name="ssma-v83"></a>SSMA v8.3

Die Version v8.3 von SSMA for Access wird um gezielte Korrekturen erweitert, die auf die Verbesserung von Qualitäts- und Konvertierungsmetriken ausgelegt sind. Darüber hinaus bietet diese Version von SSMA for Access Korrekturen, die Folgendes:

* Beheben von Barrierefreiheitsproblemen.
* Fügen Sie `hierarchyid` grundlegende Unterstützung für den Typ in SQL Server hinzu.

## <a name="ssma-v82"></a>SSMA v8.2

Die version8.2 von SSMA for Access wird um gezielte Korrekturen erweitert, die auf die Verbesserung von Qualitäts- und Konvertierungsmetriken ausgelegt sind.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.1 auf v8.2 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v81"></a>SSMA v8.1

Die version8.1 von SSMA for Access wird um gezielte Korrekturen erweitert, die auf die Verbesserung von Qualitäts- und Konvertierungsmetriken ausgelegt sind.

> [!NOTE]
> Ein bekanntes Problem mit der automatischen Aktualisierung kann den Fehler eines Updates von SSMA v8.0 auf v8.1 verursachen. Wenn dieser Fehler auftritt, laden Sie die neue Version herunter und installieren Sie sie manuell.

## <a name="ssma-v80"></a>SSMA v8.0

Die versionv8.0 von SSMA for Access wird um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern sollen. Diese Version bietet auch die folgenden neuen Funktionen:

* Unterstützung für **azure SQL Database Managed Instance** als Ziel. Sie können jetzt neue Projekte für Azure SQL Database Managed Instance erstellen:

  ![SQL DB MI-Projekt](../media/ssma-newproject-sqldbmi.png)

* Post-Conversion **Fix Advisor**. Erfahren Sie mehr darüber [hier](https://techcommunity.microsoft.com/t5/Microsoft-Data-Migration/Accelerate-your-Oracle-migrations-with-new-machine-learning/ba-p/368733).

* Vorläufige Datenbank-/Schemaauswahl.

    Beim Herstellen einer Verbindung mit der Quelle kann der Benutzer nun Datenbanken/Schemas auswählen, die von Interesse sind. Wenn Sie nur die Schemas auswählen, die Sie migrieren möchten, sparen Sie Zeit während der ersten Verbindung und verbessern die Gesamtleistung von SSMA.

   ![SSMA-Filterobjekte](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

Die Version v7.10 von SSMA for Access wird um gezielte Korrekturen erweitert, die zusätzliche Sicherheits- und Datenschutzbestimmungen bieten, um Änderungen der globalen Anforderungen gerecht zu werden.

## <a name="ssma-v79"></a>SSMA v7.9

Die Version v7.9 von SSMA for Access enthält die folgenden Änderungen:

* Gezielte Korrekturen, die die Qualitäts- und Konvertierungsmetriken verbessern.
* Unterstützung in der SSMA-Befehlszeile zum Ändern der Datentypzuordnung und der Projekteinstellungen.
* Das Dialogfeld für die Azure SQL-Datenbankverbindung in SSMA wurde ebenfalls geändert, um den vollqualifizierten Servernamen anzugeben. In früheren Versionen von SSMA musste das Präfix Azure SQL-Datenbank in den Projekteinstellungen explizit erwähnt werden.

## <a name="ssma-v78"></a>SSMA v7.8

Die Version v7.8 von SSMA for Access enthält die folgenden Änderungen:

* Änderungstypzuordnung, die in den Projekteinstellungen hervorgehoben ist.
* Die Möglichkeit für Benutzer, Telemetriedaten zu deaktivieren.

## <a name="ssma-v77"></a>SSMA v7.7

Die Version v7.7 von SSMA for Access enthält die folgenden Änderungen:

* Gezielte Korrekturen, die die Qualitäts- und Konvertierungsmetriken verbessern.
* Basierend auf der beliebten Nachfrage ist die 32-Bit-Version von SSMA for Access zurück. Im Vergleich zur vorherigen Implementierung (vor version7.4) gibt es zwei Installationspakete, die jedoch nicht nebeneinander installiert werden können. Daher müssen Sie die am besten geeignete Version basierend auf den Konnektivitätskomponenten auswählen, die Sie haben. Es ist immer vorzuziehen, die 64-Bit-Version zu verwenden, wenn möglich.

## <a name="ssma-v76"></a>SSMA v7.6

Die Version v7.6 von SSMA for Access wird um gezielte Korrekturen erweitert, die die Qualität und Konvertierungsmetriken verbessern, sowie um Unterstützung für SQL Server 2017 (öffentliche Vorschau). Die Unterstützung für SQL Server 2017 unter Windows und Linux befindet sich in der öffentlichen Vorschau und sollte nicht für Produktionsmigrationen verwendet werden.

## <a name="ssma-v75"></a>SSMA v7.5

Die Version v7.5 von SSMA for Access wurde um mehrere Verbesserungen erweitert, um eine bessere Zugänglichkeit für Menschen mit Behinderungen zu gewährleisten.

## <a name="ssma-v74"></a>SSMA v7.4

Die Version v7.4 von SSMA for Access enthält die folgenden Änderungen:

* Die **Option Abfragetimeout** ist jetzt während der Schemaobjektermittlung an Quelle und Ziel verfügbar.

  ![Abfragetimeoutoption](../media/query-timeout_red.png)

* Die Qualitäts- und Konvertierungsmetrik wurde durch gezielte Korrekturen auf Basis des Kundenfeedbacks verbessert.

  > [!IMPORTANT]
  > .NET 4.5.2 ist eine Voraussetzung für die Installation von SSMA v7.4. Darüber hinaus wurde ab version7.4 die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v73"></a>SSMA v7.3

Die Version v7.3 von SSMA for Access enthält die folgenden Änderungen:

* Verbesserte Qualitäts- und Konvertierungsmetrik mit gezielten Korrekturen basierend auf Kundenfeedback.
* SSMA-Erweiterbarkeitsframework, das über die folgenden Elemente verfügbar gemacht wird:
  * Exportieren sie die Funktionalität in ein SQL Server Data Tools (SSDT)-Projekt.
    * Sie können jetzt Schemaskripts aus SSMA in ein SSDT-Projekt exportieren. Sie können die Schemaskripts verwenden, um zusätzliche Schemaänderungen vorzunehmen und die Datenbank bereitzustellen.

        ![Speichern als SSDT-Projektbefehl](../media/export-schema-scripts_red.png)
  * Bibliotheken, die von SSMA für die Durchführung benutzerdefinierter Konvertierungen verwendet werden können.
    * Sie können jetzt Code erstellen, der benutzerdefinierte Syntaxkonvertierungen und Konvertierungen verarbeiten kann, die zuvor nicht von SSMA verarbeitet wurden.
      * Anweisungen zum Erstellen eines benutzerdefinierten [Konverters](https://techcommunity.microsoft.com/t5/Microsoft-Data-Migration/Extending-SQL-Server-Migration-Assistant-s-conversion/ba-p/1004181)sowie eines Beispielprojekts für die Konvertierung finden Sie im Blogbeitrag Extending SQL Server Migration Assistant es Conversion Capabilities .

## <a name="ssma-v72"></a>SSMA v7.2

Die Version v7.2 von SSMA for Access enthält die folgenden Änderungen:

* Verbesserte Qualitäts- und Konvertierungsmetrik mit gezielten Korrekturen basierend auf Kundenfeedback.
* Telemetrieverbesserungen, um bessere Datenpunkte bereitzustellen, um Kundenprobleme zu beheben und die Conversion-Raten von SSMA zu verbessern.

## <a name="ssma-v71"></a>SSMA v7.1

Die version7.1-Version von SSMA for Access enthält die folgenden Änderungen:

* SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Diese Funktion befindet sich in der technischen Vorschau und unterstützt die Schema- und Datenverschiebung auf SQL-Clients.
* SSMA unterstützt jetzt automatische Updates, um die neueste Version von SSMA herunterzuladen, sobald es verfügbar ist.
* SSMA installierbare Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) bereitgestellt.

## <a name="may-2016"></a>Mai 2016

Die Version von SSMA for Access vom Mai 2016 enthält die folgenden Änderungen:

* Offizielle Unterstützung für SQL Server 2016 wurde hinzugefügt.
* Installationsüberprüfung für .NET 2.0 entfernt.
* Behoben `save-project` `open-project` und Befehle für SSMA-Konsole.
* Fester `securepassword` Befehl für SSMA Console.
* Die Zählung der Objekte für die Erstbeladung wurde behoben.
* Feste Tabellen Daten laden für UI-Registerkarten für Zugriff.
* Fehler in globalen Einstellungen behoben.

## <a name="march-2016"></a>März 2016

Die Vorschauversion von SSMA for Access vom März 2016 bietet Unterstützung für die Migration zu SQL Server 2016.

## <a name="january-2016"></a>Januar 2016

Die Wartungsversion von SSMA for Access vom Januar 2016 enthält die folgenden Änderungen:

* Invalide Funktion für standardeinstellung eines GUID-Feldes behoben (RFC 3894811).
* Beim Importieren von Datensätzen in SQL-Datenbank (Azure) (RFC 4919573) wurde behoben.
* Ansichtsprotokollmenüelement zu SSMA hinzugefügt (RFC 5706203).
* Telemetrie wurde hinzugefügt.

## <a name="july-2014"></a>Juli 2014

Die Version von SSMA for Access vom Juli 2014 enthält die folgenden Änderungen:

* Verbesserte Azure SQL DB-Codekonvertierung.
* Erweiterungspaketfunktionalität in Schema verschoben, um Azure SQL DB zu unterstützen.
* Getestete Leistungsverbesserungen für Datenbanken mit über 10k-Objekten.
* UI-Verbesserungen für den Umgang mit einer großen Anzahl von Objekten hinzugefügt.
* Unterstützung für die Hervorhebung von "bekannten" LOB-Schemas hinzugefügt (damit sie bei der Konvertierung ignoriert werden können).
* Verbesserung der Konvertierungsgeschwindigkeit wurde hinzugefügt.
* Unterstützung für die Anzeige von Objektanzahlen in der Benutzeroberfläche wurde hinzugefügt.
* Die Berichtsgröße wurde um mehr als 25 % reduziert.
* Verbesserte Fehlermeldungen für nicht analysierte Konstrukte.

## <a name="april-2014"></a>April 2014

Die Version von SSMA for Access vom April 2014 enthält die folgenden Änderungen:

* Unterstützung für MS SQL Server 2014 wurde hinzugefügt.
* Fehler im Zusammenhang mit der Konvertierung in Azure wurden behoben.
* Fehler im Zusammenhang mit unsichtbaren Berichtsseiten in IE 10 wurden behoben.

## <a name="january-2012"></a>Januar 2012

Die Version von SSMA for Access vom Januar 2012 enthält die folgenden Änderungen:

* Es wurde die Option bereitgestellt, benutzername und kennwortfür verknüpfte MS Access-Tabellen nach der Migration nicht beizubehalten.
* Legen Sie Kaskadenaktionen für Zirkelverweise auf Keine Aktion fest.
* Vorausgesetzt, dass ordnungsgemäße Meldungen, die kaskadierte Aktionen für Zirkelverweise anzeigen, auf Keine Aktion festgelegt wurden.

## <a name="july-2011"></a>Juli 2011

Die Version von SSMA for Access vom Juli 2011 fügt eine verbesserte Fehlerberichterstattung während der Datenmigration hinzu.

## <a name="april-2011"></a>Januar 2011

Die Version von SSMA for Access vom April 2011 enthält die folgenden Änderungen:

* Es wurde eine einzelne installierbare Datei von [!INCLUDE [ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)]"SSMA for Access" hinzugefügt, die unterstützt , und [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)] Azure SQL.
* Es wurde die [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]Möglichkeit hinzugefügt, eine Verbindung mit herzustellen.
* SSMA für Access Console-Versionsunterstützung für Abwärtskompatibilität hinzugefügt. Sie können die Projekte öffnen, die von Versionen zuvor in SSMA v5.0 erstellt wurden.
* Es wurde die Möglichkeit hinzugefügt, SSMA v5.0 Produkt nebeneinander (SxS) mit älteren Versionen von SSMA Product zu installieren.

## <a name="july-2010"></a>Juli 2010

Die Version von SSMA for Access vom Juli 2010 enthält die folgenden Änderungen:

* Unterstützung für die Migration zu SQL Server 2008 R2 und Azure SQL wurde hinzugefügt.
* Es wurde eine sichere Verbindung zu SQL Server und Azure SQL hinzugefügt.
* Unterstützung für Access 2010-Datenbanken wurde hinzugefügt.
* Es wurde eine neue SSMA-Konsolenanwendung für die Ausführung von Befehlszeilen hinzugefügt.
* Unterstützung für den `DateTime2` SQL Server-Datentyp wurde hinzugefügt.

## <a name="june-2008"></a>Juni 2008

Die Version von SSMA for Access vom Juni 2008 bietet Unterstützung für Access 2007-Datenbanken.

## <a name="may-2007"></a>Mai 2007

Die Version von SSMA for Access vom Mai 2007 enthält die folgenden Änderungen:

* Unterstützung für Access-Datenbanken hinzugefügt, die Arbeitsgruppenrichtlinien verwenden.
* Vorausgesetzt, die Möglichkeit, konvertierte Objekte aus dem SQL Server-Metadaten-Explorer zu löschen.
* Unterstützung für vom Benutzer eingegebene Kommentare im SQL Server-formatierten SQL-Modus hinzugefügt.
* Verbesserungen bei der Objektkonvertierung hinzugefügt.

## <a name="november-2006"></a>Januar 2006

Die Version von SSMA for Access vom November 2006 enthält die folgenden Änderungen:

* Es wurde ein neuer Datenbankmigrations-Assistent hinzugefügt, der Sie [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)]durch die Migration einer einzelnen Datenbank von Access nach führt.
* Es wurde ein neuer Befehl Konvertieren, Laden und Migrieren hinzugefügt, der Access-Datenbanken konvertiert, die konvertierten Objekte in [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)], lädt und Daten in einem Schritt in [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)] alle migriert.
* Verbesserte Abfragemigration. Die Abfragemigration konvertiert jetzt mehr SELECT-Abfragen in Ansichten. Weitere Informationen finden Sie unter [Konvertieren von Zugriffsdatenbankobjekten](converting-access-database-objects-accesstosql.md).
* Es wurde die Möglichkeit hinzugefügt, [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen- und Indexeigenschaften auf der Registerkarte **Tabelle** zu bearbeiten.
* Neue globale Einstellungen hinzugefügt:
  * Sie können Liniennummern in Editorfenstern anzeigen.
  * Sie können SSMA so konfigurieren, dass doppelte Objekte ersetzt werden oder duplikate Objekte während der Schemakonvertierung immer oder nie ersetzt werden.
* Es wurde eine neue Konvertierungsoption hinzugefügt, mit der Sie angeben können, ob SSMA eine Warnung anzeigt, wenn eine komplexe Abfrage einen Platzhalter enthält.

## <a name="july-2006"></a>Januar 2006

Die Veröffentlichung von SSMA for Access im Juli 2006 war die erste Version.
