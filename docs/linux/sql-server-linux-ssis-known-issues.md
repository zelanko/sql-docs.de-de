---
title: Einschränkungen und bekannte Probleme für SSIS unter Linux | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, Einschränkungen und bekannte Probleme für SQL Server Integration Services (SSIS) auf Linux-Computern
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 06/06/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 33f798fd3b7816cae61137292392cb9cca729ec7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020599"
---
# <a name="limitations-and-known-issues-for-ssis-on-linux"></a>Einschränkungen und bekannte Probleme für SSIS unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel beschreibt Einschränkungen und bekannte Probleme für SQL Server Integration Services (SSIS) für Linux.

## <a name="general-limitations-and-known-issues"></a>Allgemeine Einschränkungen und bekannte Probleme

Die folgenden Funktionen werden in dieser Version von SSIS unter Linux nicht unterstützt:
  - SSIS-Katalogdatenbank
  - Geplante paketausführung vom SQL-Agent
  - Windows-Authentifizierung
  - Drittanbieter-Komponenten
  - Change Data Capture (CDC)
  - SSIS Scale Out-
  - Azure FeaturePack für SSIS
  - Hadoop und HDFS-Unterstützung
  - Microsoft Connector for SAP BW

Weitere Einschränkungen und bekannte Probleme mit SSIS unter Linux, finden Sie unter den [– Anmerkungen zu dieser](sql-server-linux-release-notes.md#ssis).

## <a name="components"></a> Unterstützte und nicht unterstützte Komponenten

Die folgenden integrierten Integration Services-Komponenten werden unter Linux unterstützt. Einige davon gelten Einschränkungen für die Linux-Plattform. Integrierte Komponenten, die hier nicht aufgeführt sind, werden unter Linux nicht unterstützt.

## <a name="supported-control-flow-tasks"></a>Ablaufsteuerungstasks unterstützt
- Masseneinfügungstask
- Datenflusstask
- Datenprofilerstellungs-Task
- SQL ausführen (Task)
- T-SQL-Anweisung ausführen (Task)
- Task 'Ausdruck'
- FTP-Task
- Webdienst (Task)
- XML-Task

## <a name="control-flow-tasks-supported-with-limitations"></a>Ablaufsteuerungstasks, die mit Einschränkungen unterstützt

| Task | Einschränkungen |
|------------|---|
| Task Prozess ausführen | Nur unterstützt in-Process-Modus. |
| Task "Dateisystem" | Die *verschieben Directory* und *Festlegen von Dateiattributen* Aktionen werden nicht unterstützt. |
| Skripttask | Unterstützt nur standard .NET Framework-APIs. |
| Mail senden (Task) | Unterstützt nur anonyme Benutzer-Modus. |
| Der Task Datenbanken übertragen | UNC-Pfade werden nicht unterstützt. |
| | |

## <a name="supported-and-unsupported-maintenance-plan-tasks"></a>Unterstützte und nicht unterstützte Wartungsplantasks

In einem SQL Server-Wartungsplan können Sie in der Regel eine Vielzahl von SSIS-Tasks verwenden.

Die folgenden Wartungsplantasks sind unter Linux nicht unterstützt:
- Operator benachrichtigen
- Führen Sie SQL Server-Agent-Auftrag

Die folgenden Wartungsplantasks sind unter Linux unterstützt:
- Datenbankintegrität überprüfen
- Datenbank verkleinern
- Index neu organisieren
- Index neu erstellen
- Statistikaktualisierung
- Verlaufscleanup
- Datenbank sichern
- T-SQL-Anweisung

## <a name="supported-control-flow-containers"></a>Ablaufsteuerungscontainer unterstützt
- Sequenzcontainer
- For-Schleifencontainer
- Foreach-Schleifencontainer

## <a name="supported-data-flow-sources-and-destinations"></a>Flow für unterstützte Datenquellen und Ziele
- Rohdatendatei-Quelle und Ziel
- XML-Quelle

## <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>Flow-Datenquellen und Ziele, die mit Einschränkungen unterstützt

| Komponente | Einschränkungen |
|------------|---|
| ADO NET-Quelle und Ziel | Unterstützt nur den SQLClient-Datenanbieter. |
| Flatfilequelle und das Ziel | Unterstützt nur Windows-Stil Dateipfade, auf die die standardmäßige Zuordnung Pfadregel angewendet wird. Z. B. `D:\home\ssis\travel.csv` wird `/home/ssis/travel.csv`. |
| OData-Quelle | Unterstützt nur die Standardauthentifizierung. |
| ODBC-Quelle und -Ziel | Unterstützt die 64-Bit-Unicode-ODBC-Treiber unter Linux. Hängt von der UnixODBC-Treiber-Manager unter Linux. |
| OLE DB-Quelle und Ziel | Unterstützt nur SQL Server Native Client 11.0 und Microsoft OLE DB-Anbieter für SQL Server ein. |
| | |

## <a name="supported-data-flow-transformations"></a>Datenflusstransformationen unterstützt
- Aggregat
- Überwachen von
- Balanced Data Distributor
- Zeichenzuordnung
- Bedingtes Teilen
- Kopieren von Spalten
- Datenkonvertierung
- Abgeleitete Spalte
- Exportieren von Spalten
- Fuzzygruppierung
- Fuzzysuche
- Importieren von Spalten
- Suche
- Merge
- Merge Join
- Multicast
- Pivotieren
- Zeilenanzahl
- Langsam veränderliche Dimensionen
- Sort
- Ausdruckssuche
- Union All
- Entpivotieren

## <a name="data-flow-transformations-supported-with-limitations"></a>Datenflusstransformationen, die mit Einschränkungen unterstützt

| Komponente | Einschränkungen |
|------------|---|
| Transformation für OLE DB-Befehl | Dieselben Einschränkungen wie bei den OLE DB-Quelle und Ziel. |
| Skriptkomponente | Unterstützt nur standard .NET Framework-APIs. |
| | |

## <a name="supported-and-unsupported-log-providers"></a>Unterstützte und nicht unterstützte Protokollanbieter
Alle die integrierte SSIS-Protokollanbieter für Linux unterstützt werden, mit Ausnahme der Windows-Ereignisprotokollprovider.

Der Protokollanbieter für SQL Server unterstützt nur die SQL-Authentifizierung; Er unterstützt keine Windows-Authentifizierung.

Die SSIS-Protokollanbieter für Textdateien, XML-Dateien, und für SQL Server Profiler schreiben ihre Ausgabe in eine Datei, die Sie angeben. Die folgenden Überlegungen gelten für den Dateipfad:
-   Wenn Sie einen Pfad angeben, schreibt der Protokollanbieter, auf das aktuelle Verzeichnis des Hosts. Wenn der aktuelle Benutzer nicht über Schreibberechtigung für das aktuelle Verzeichnis des Hosts verfügt, löst der Protokollanbieter einen Fehler aus.
-   Sie können nicht auf eine Umgebungsvariable in einem Dateipfad verwenden. Wenn Sie eine Umgebungsvariable angeben, wird die Literale Text, den Sie angeben im Dateipfad angezeigt. Wenn Sie angeben, z. B. `%TMP%/log.txt`, der Protokollanbieter fügt den Literaltext `/%TMP%/log.txt` auf das aktuelle Hostverzeichnis.

## <a name="related-content-about-ssis-on-linux"></a>Verwandte Inhalte zu SSIS unter Linux
-   [Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS](sql-server-linux-migrate-ssis.md)
-   [Installieren von SQL Server Integration Services (SSIS) unter Linux](sql-server-linux-setup-ssis.md)
-   [Konfigurieren von SQL Server Integration Services unter Linux mit Ssis-conf](sql-server-linux-configure-ssis.md)
-   [Zeitplan SQL Server Integration Services-paketausführung unter Linux mit cron](sql-server-linux-schedule-ssis-packages.md)
