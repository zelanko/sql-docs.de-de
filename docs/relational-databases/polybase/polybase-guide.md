---
title: PolyBase-Leitfaden | Microsoft-Dokumentation
ms.date: 05/31/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: quickstart
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- Hadoop import
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c31f9538f3429ff4ae1182ee0cd974996cc705a6
ms.sourcegitcommit: 82bb56269faf3fb5dd1420418e32a0a6476780cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "43694723"
---
# <a name="polybase-guide"></a>PolyBase-Leitfaden

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]

PolyBase ermöglicht Ihrer SQL Server 2016-Instanz das Verarbeiten von Transact-SQL-Abfragen, die Daten aus Hadoop lesen. Die gleiche Abfrage kann auch auf relationale Tabellen in SQL Server zugreifen. Mit PolyBase kann dieselbe Abfrage auch die Daten aus Hadoop und SQL Server verknüpfen. In SQL Server stellt eine [externe Tabelle](../../t-sql/statements/create-external-table-transact-sql.md) oder [externe Datenquelle](../../t-sql/statements/create-external-data-source-transact-sql.md) die Verbindung mit Hadoop bereit.

PolyBase bietet dieselben Funktionen für die folgenden SQL-Produkte von Microsoft:

- SQL Server 2016 und höhere Versionen
- Analytics Platform System (ehemals Parallel Data Warehouse)
- Azure SQL Data Warehouse

PolyBase überträgt einige Berechnungen per Push an den Hadoop-Knoten, um die Abfrage insgesamt zu optimieren. Der externe PolyBase-Zugriff ist jedoch nicht auf Hadoop beschränkt. Andere unstrukturierte nicht relationale Tabellen werden ebenfalls unterstützt, z.B. durch Trennzeichen getrennte Textdateien.

#### <a name="data-import-and-export"></a>Importieren und Exportieren von Daten

Durch die zugrunde liegende Unterstützung von PolyBase können T-SQL-Abfragen außerdem Daten aus Azure Blob Storage importieren und exportieren. PolyBase ermöglicht Azure SQL Data Warehouse zudem das Importieren und Exportieren von Daten aus Azure Data Lake Store und aus Azure Blob Storage.

Informationen zur Verwendung von PolyBase finden Sie unter [Erste Schritte mit PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).
  
![PolyBase logical](../../relational-databases/polybase/media/polybase-logical.png "PolyBase logical")

## <a name="why-use-polybase"></a>Gründe für die Verwendung von PolyBase

In der Vergangenheit war es schwieriger, Ihre SQL Server-Daten mit externen Daten zu verknüpfen. Ihnen standen die beiden folgenden unpraktischen Optionen zur Auswahl:

- Übertragen der Hälfte Ihrer Daten, damit all Ihre Daten in dem einen oder in dem anderen Format vorliegen.
- Abfragen beider Datenquellen und Schreiben benutzerdefinierter Abfragelogik zum Verknüpfen und Integrieren der Daten auf Clientebene.

Mit PolyBase vermeiden Sie diese beiden Optionen, indem Sie die Daten mithilfe von T-SQL verknüpfen.

Einfach ausgedrückt: Mit PolyBase müssen Sie keine zusätzliche Software in Ihrer Hadoop-Umgebung installieren. Sie fragen externe Daten anhand der gleichen T-SQL-Syntax ab, die auch zum Abfragen einer Datenbanktabelle verwendet wird. Alle von PolyBase implementierten Unterstützungsaktionen werden transparent durchgeführt. Der Abfrageautor benötigt keine Hadoop-Kenntnisse.

Vorzüge von PolyBase:

- **Abfragen von in Hadoop gespeicherten Daten von SQL Server oder PDW.** Benutzer speichern Daten in kostengünstigen verteilten und skalierbaren Systemen, wie z.B. Hadoop. PolyBase vereinfacht die Abfrage der Daten mithilfe von T-SQL.

- **Abfragen von in Azure Blob Storage gespeicherten Daten.** Ein Azure-Blobspeicher ist eine bequeme Möglichkeit, Daten zu speichern, die von Azure-Diensten verwendet werden.  PolyBase vereinfacht den Zugriff auf die Daten mithilfe von T-SQL.

- **Importieren von Daten aus Hadoop, Azure Blob Storage oder Azure Data Lake Store.** Profitieren Sie von der Geschwindigkeit der Columnstore-Technologie und den Analysefunktionen von Microsoft SQL, indem Sie Daten aus Hadoop, Azure Blob Storage oder Azure Data Lake Store in relationale Tabellen importieren. Sie benötigen keine separaten ETL-Funktionen und kein Importtool.

- **Exportieren von Daten in Hadoop, Azure-Blobspeicher oder Azure Data Lake Store.** Archivieren Sie Daten in Hadoop, Azure-Blobspeichern oder Azure Data Lake Store, um kostengünstigen Speicherplatz zu nutzen und Daten für einfachen Zugriff online zu halten.

- **Integrieren in BI-Tools.** Verwenden Sie PolyBase zusammen mit den Business Intelligence- und Analysfunktionen von Microsoft, oder verwenden Sie beliebige Drittanbietertools, die mit SQL Server kompatibel sind.

## <a name="performance"></a>Leistung

- **Übertragen von Berechnungen an Hadoop.** Der Abfrageoptimierer trifft eine kostenbasierte Entscheidung darüber, ob die Berechnung an Hadoop übertragen wird, um die Abfrageleistung zu verbessern.  Für diese kostenbasierte Entscheidung verwendet der Optimierer Statistiken in externen Tabellen. Bei der Übertragung der Berechnung werden MapReduce-Aufträge erstellt und die verteilten Berechnungsressourcen von Hadoop genutzt.

- **Skalieren von Berechnungsressourcen.** Um die Abfrageleistung zu verbessern, können Sie [PolyBase-Erweiterungsgruppen](../../relational-databases/polybase/polybase-scale-out-groups.md)von SQL Server verwenden. Die ermöglicht eine parallele Datenübertragung zwischen SQL Server-Instanzen und Hadoop-Knoten und fügt Berechnungsressourcen für die Verarbeitung der externen Daten hinzu.

## <a name="polybase-guide-topics"></a>PolyBase-Leitfaden – Themen

Dieser Leitfaden enthält Themen, die Sie bei der effizienten und effektiven Verwendung von PolyBase unterstützen.

|||
|-|-|
|**Thema**|**Beschreibung**|
|[Erste Schritte mit PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)|Grundlegende Schritte zum Installieren und Konfigurieren von PolyBase. Dieses Thema zeigt Ihnen, wie Sie externe Objekte erstellen, die auf Daten in Hadoop oder Azure-Blobspeichern zeigen, und enthält Abfragebeispiele.|
|[Zusammenfassung der PolyBase-Funktionen mit Versionsangabe](../../relational-databases/polybase/polybase-versioned-feature-summary.md)|Beschreibt die PolyBase-Funktionen, die in SQL Server, SQL-Datenbank und SQL Data Warehouse unterstützt werden.|
|[PolyBase-Erweiterungsgruppen](../../relational-databases/polybase/polybase-scale-out-groups.md)|Horizontales Skalieren der Parallelität zwischen SQL Server und Hadoop durch Verwenden von SQL-Server-Erweiterungsgruppen.|
|[PolyBase-Installation](../../relational-databases/polybase/polybase-installation.md)|Referenz und Schritte zur Installation von PolyBase mit dem Installations-Assistenten oder über ein Befehlszeilentool.|
|[PolyBase-Konfiguration](../../relational-databases/polybase/polybase-configuration.md)|Konfigurieren der SQL Server-Einstellungen für PolyBase.  Beispiel: Konfigurieren von Berechnungsweitergabe und Kerberos-Sicherheit.|
|[PolyBase T-SQL-Objekte](../../relational-databases/polybase/polybase-t-sql-objects.md)|Erstellen der T-SQL-Objekte, die PolyBase verwendet, um externe Daten zu definieren und darauf zuzugreifen.|
|[PolyBase-Abfragen](../../relational-databases/polybase/polybase-queries.md)|Verwenden von T-SQL-Anweisungen zum Abfragen, Importieren oder Exportieren externer Daten.|
|[Problembehandlung in PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md)|Techniken zum Verwalten von PolyBase-Abfragen. Verwenden von dynamischen Verwaltungssichten (Dynamic Management Views, DMVs) zum Überwachen von PolyBase-Abfragen sowie Informationen zum Lesen eines PolyBase-Abfrageplans, um Leistungsengpässe zu ermitteln.|
| &nbsp; | &nbsp; |
  
