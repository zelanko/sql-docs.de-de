---
title: Neuerungen in SSMA für MySQL (MySQLToSql)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 09/22/2018
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1451a0b0-6713-4d0c-954f-ea3d8fce1d31
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b927d9116424f1b471dc675189548e3c6a459569
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52531756"
---
# <a name="whats-new-in-ssma-for-mysql-mysqltosql"></a>Neuerungen in SSMA für MySQL (MySqlToSql)
In diesem Artikel werden die SSMA für MySQL-Änderungen in jeder Version aufgelistet. 

## <a name="ssma-v710"></a>SSMA v7.10
Die Version v7.10 von SSMA für MySQL enthält die folgenden Änderungen:
- Gezielte Fixes soll, geben Sie zusätzliche Sicherheits- und Datenschutzfunktionen, um Änderungen in globalen Anforderungen zu erfüllen.
- Ein Fix für die Konvertierung von Leerzeichen zwischen den Namen und Argumenten Funktionsliste.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v79"></a>SSMA v7.9
Die Version v7.9 von SSMA für MySQL enthält die folgenden Änderungen:
- Gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern.
- Teilweise Unterstützung für die Migration von Typen von räumlichen Daten aus MySQL in Azure SQL-Datenbank.
- Unterstützt die in der SSMA-Befehlszeile, Data Type Mapping und Projekt-Einstellungen zu ändern.
- Unterstützung für die Migration von Daten mithilfe von SQL Server Integration Services (SSIS). Nach der Konvertierung des Schemas ist es möglich, ein SSIS-Paket mit einer Option für das Kontextmenü zu erstellen.
- Die Azure SQL-Datenbank-Verbindungsdialogfeld in SSMA wurde auch geändert, um den vollqualifizierten Servernamen angeben. In früheren Versionen von SSMA musste das Präfix für die Azure SQL-Datenbank innerhalb von Projekten Einstellungen angegeben werden.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v78"></a>SSMA V7. 8
Die V7. 8-Version von SSMA für MySQL enthält die folgenden Änderungen:
- Hervorgehobene Änderung Typzuordnung in den Projekteinstellungen.
- Die Möglichkeit für Benutzer zum Deaktivieren der Telemetrie wird bereitgestellt.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v77"></a>SSMA v7.7
Die Version v7.7 von SSMA für MySQL enthält die folgenden Änderungen:
- SSMA für MySQL wurde mit gezielte Fixes verbessert die Qualität und Konvertierung von Metriken zu verbessern.
- Basierend auf der großen Nachfrage, ist die 32-Bit-Version von SSMA für MySQL zurück. Im Vergleich zu der vorherigen Implementierung (vor v7.4), es gibt zwei Installationspakete, aber sie können nicht parallel installiert werden. Daher müssen Sie die am besten geeignete Version auf Grundlage der Konnektivitätskomponenten benötigen Sie auswählen. Es ist immer besser, nach Möglichkeit die 64-Bit-Version zu verwenden.
- SSMA für MySQL verfügt jetzt über ODBC-Verbindungszeichenfolge-Verbindungsmodus, sodass Sie keine ODBC-Treiber von Drittanbietern verwenden, die mit MySQL kompatibel sind.

> [!IMPORTANT]
> SSMA v7.4 und höher ist .net 4.5.2 eine Voraussetzung für Installation.

## <a name="ssma-v76"></a>SSMA v7.6
Die Version v7.6 von SSMA für MySQL wurde verbessert, gezielte Fixes, die die Qualität und Konvertierung von Metriken zu verbessern und mit Unterstützung für SQL Server 2017 (öffentliche Vorschau). Unterstützung für SQL Server 2017 unter Windows und Linux wird in der öffentlichen Vorschau und sollte nicht für Produktionsmigrationen verwendet werden.

> [!IMPORTANT]
> SSMA v7.4 und höher .net 4.5.2 ist eine Voraussetzung für Installation, und die 32-Bit-Version des Tools wurde eingestellt.

## <a name="ssma-v75"></a>SSMA V7. 5
Die V7. 5-Version von SSMA für MySQL wurde mit verschiedene Verbesserungen, um sicherzustellen, dass größere Barrierefreiheit für Personen mit behinderungen verbessert.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA V7. 5. Darüber hinaus wird v7.4 ab, die 32-Bit-Version von SSMA eingestellt.

## <a name="ssma-v74"></a>SSMA v7.4
Die Version v7.4 von SSMA für MySQL enthält die folgenden Änderungen:
- Die **Abfragetimeout** Option ist während der Ermittlung an Quelle und Ziel am Schema jetzt verfügbar.
![Option Timeout für Remoteabfragen](../media/query-timeout_red.png)
- Die Qualität und Konvertierung-Metrik wurde durch gezielte Fixes, basierend auf Kundenfeedback verbessert.

> [!IMPORTANT]
> .NET 4.5.2 ist eine Voraussetzung zum Installieren von SSMA-v7.4. Darüber hinaus wird v7.4 ab, die 32-Bit-Version von SSMA eingestellt. 

## <a name="ssma-v73"></a>SSMA V7. 3
Die V7. 3-Version von SSMA für MySQL enthält die folgenden Änderungen:
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
Die V7. 2-Version von SSMA für MySQL enthält die folgenden Änderungen:
- Verbesserte Qualität und Konvertierung Metrik mit gezielte Fixes, die basierend auf Kundenfeedback.
- Telemetrie Erweiterungen besser Datenpunkte zum Behandeln von Kundenproblemen und Verbessern SSMAs-Abschlussraten bereit.

## <a name="ssma-v71"></a>SSMA v7.1
Die v7.1-Version von SSMA für Access umfasst die folgenden Änderungen:
- SQL Server 2017 unter Windows und Linux CTP1 ist jetzt eine unterstützte Zielplattform für die Migration. Dieses Feature ist in der technischen Vorschau und ermöglicht die Verlagerung von Schema und Daten an SQL-Zielserver.
- SSMA unterstützt jetzt die automatische Updates für die neueste Version von SSMA herunterladen, sobald diese verfügbar ist.
- Installierbare SSMA-Binärdateien werden jetzt über Windows Installer-Paketdateien (.msi) übermittelt.

**Ressourcen**

[Erweitern von SQL Server Migration Assistant Funktionen](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Bewerten und Migrieren von Daten aus nicht-Microsoft-datenplattformen mit SQL Server *(mit der Oracle-Beispiel)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Mai 2016  
Die Version Mai 2016 von SSMA für MySQL umfasst die folgenden Änderungen:.

-  Unterstützung für SQL Server 2016 hinzugefügt.
-  Verbesserte Parser und Auflösung.
-  Entfernt die Überprüfung der Installer für .net 2.0.
-  Aktualisierte Erweiterungspaket Abhängigkeit von .net 3.5 zu .net 4.0.
-  Feste BigInt Typemapping für MySql.
-  Feste "Speichern" Projekt"und"Projekt öffnen"-Befehle für SSMA-Konsole.
-  Feste "Securepassword"-Befehl für SSMA-Konsole.
-  Korrektur von Objekten für das anfängliche laden zählen.
-  Feste MsSql-Objekte werden geladen.
-  Korrektur von Bug in den globalen Einstellungen.
 
## <a name="march-2016"></a>März 2016  
Die vom März 2016 Preview-Version von SSMA für MySQL enthält die folgenden Änderungen:  
  
-  Unterstützung für die Migration zu SQL Server 2016. 
  
## <a name="january-2016"></a>Januar 2016  
Die Version für den Wartungsmodus Januar 2016 von SSMA für MySQL enthält die folgenden Änderungen:  
  
-  Hinzugefügte Ansicht der Protokoll-Menüelement, SSMA (RFC 5706203).  
-  Zusätzliche Telemetriedaten.  
  
## <a name="july-2014"></a>Juli 2014  
Die Version von Juli 2014 von SSMA für MySQL enthält die folgenden Änderungen:  
  
-  Verbesserte codekonvertierung für Azure SQL-Datenbank. 
-  Pack-Funktionalität von Erweiterungen, die in Schema zur Unterstützung von Azure SQL-Datenbank verschoben werden.  
-  Leistungsverbesserungen, die für Datenbanken mit mehr als 10 KB Objekten getestet.  
-  Verbesserungen der Benutzeroberfläche für den Umgang mit großen Anzahl von Objekten.  
-  Die Hervorhebung von "bekannte" LOB-Schemas (sodass sie bei der Konvertierung ignoriert werden können).  
-  Verbesserungen bei der Geschwindigkeit der Konvertierung.  
-  Zeigen Sie, dass das Objekt enthält die Benutzeroberfläche.  
-  Verringerung der Größe von mehr als 25 % zu melden.  
-  Verbesserte Fehlermeldungen für nicht verarbeitete Konstrukte.  
  
## <a name="april-2014"></a>April 2014  
Die vom Juli 2011-Version von SSMA für MySQL enthält die folgenden Änderungen:  
  
-  Die Unterstützung von MS SQL Server 2014.  
-  Behobenen Problemen in Bezug auf die Konvertierung in Azure  
-  Behobenen Problemen in Bezug auf unsichtbare Berichtsseiten in Internet Explorer 10.  
  
## <a name="july-2011"></a>Vom Juli 2011  
Die vom Juli 2011-Version von SSMA für MySQL enthält die folgenden Änderungen:  
  
-   Unterstützung für die Konvertierung des GRENZWERTS zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali" zu versetzen.  
-   Verbesserte fehlerberichterstellung während der Datenmigration.  
  
## <a name="april-2011"></a>April 2011  
Die April 2011-Version von SSMA für MySQL enthält die folgenden Änderungen:  
  
-   Einzelne installierbare "SSMA für MySQL", die unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali" und Azure SQL.  
-   Die Fähigkeit zum Verbinden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali".  
-   Verbesserte clientseitige Data Migration-Modul mit Unterstützung parallele Migration von Daten.  
-   Verbesserte Migration datenleistung mit einfachen und Bulk protokolliert Wiederherstellungsmodelle.  
-   SSMA für MySQL Console-Version unterstützt die Abwärtskompatibilität zu gewährleisten. Sie können die von früher in SSMA V5. 0-Versionen erstellte Projekte öffnen.  
-   SSMA für MySQL V5. 0-Produkt sein kann werden parallele (SxS) mit älteren Versionen von SSMA-Produkt installiert.  
  
## <a name="july-2010"></a>Juli 2010  
Die Version vom Juli 2010 von SSMA für MySQL enthält die folgenden Funktionen:  
  
1.  **Verbesserungen bei der Benutzeroberfläche:**  
  
    -   Registerkarte "SQL-Modi" MySQL-Datenbank-Objekte  
    -   Registerkarte "Einstellungen" MySQL-Datenbank-Objekte  
    -   Registerkarte "Daten" für MySQL-Tabellen  
    -   Aktualisierte Projekteinstellungen in die Konvertierung und Migration von Seiten  
    -   "Data Migration Settings" auf Tabellenebene  
  
2.  **Verbesserungen bei der Verbindung mit MySQL und SQLServer:**  
  
    -   SSL-Verbindungen in MySQL  
    -   Verschlüsselte Verbindungen in SQLServer  
  
3.  **Verbesserungen bei der MySQL-Metabase Explorer:**  
  
    -   Laden alle Objekte der MySQL-Datenbank und die entsprechenden Registerkarten.  
  
4.  **Verbesserungen bei der Konvertierung des Objekts:**  
  
    -   Die Konvertierung von MySQL-Metabase Objekten - Prozeduren, Funktionen, Sichten, Trigger und Anweisungen.  
    -   Eingeschränkte Unterstützung für räumliche Datentypen in Tabellen.  
    -   Option zum Konvertieren von MySQL-Funktionen in SQL Server gespeicherte Prozeduren  
    -   Option, um SQL-Modi und Charset-Zuordnung während der Objektkonvertierung übernehmen  
  
5.  **Verbesserungen bei der Datenmigration:**  
  
    -   Unterstützung für die Datenmigration mit serverseitigen und clientseitigen Data Migration-Engines  
    -   Unterstützung für die Migration von räumlichen Daten  
    -   Benutzerdefinierte SQL für die Datenmigration für Tabellen  
  
6.  **SSMA für MySQL-Konsole:**  
  
    -   Unterstützung von Konsolenfunktion für SSMA für MySQL  
    -   Unterstützung für Skriptebene Schnittstelle  
  
## <a name="january-2010"></a>Januar 2010  
Die Januar 2010-Version von SSMA für MySQL war die erste Version. Sie enthalten die folgenden Funktionen:  
  
-   Unterstützung für die Migration sowohl auf lokale SQL Server und Azure SQL.  
  
-   **Feature-Momentaufnahme:** Schema- und Datenmigration von Tabellen/Indizes/Einschränkungen MySQL.
