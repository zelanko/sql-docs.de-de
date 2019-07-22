---
title: Was ist PolyBase? | Microsoft-Dokumentation
ms.date: 06/10/2019
ms.prod: sql
ms.technology: polybase
ms.topic: overview
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
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: aboke
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions||>=aps-pdw-2016||=azure-sqldw-latest'
ms.openlocfilehash: 1e4818e153e9fe632d4341afb8845aceb7fd6142
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062222"
---
# <a name="what-is-polybase"></a>Was ist PolyBase?

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]

<!--SQL Server 2016/2017-->
::: moniker range="= sql-server-2016 || = sql-server-2017 || >= aps-pdw-2016 || = azure-sqldw-latest"

PolyBase ermöglicht Ihrer SQL Server 2016-Instanz das Verarbeiten von Transact-SQL-Abfragen, die Daten aus Hadoop lesen. Die gleiche Abfrage kann auch auf relationale Tabellen in SQL Server zugreifen. Mit PolyBase kann dieselbe Abfrage auch die Daten aus Hadoop und SQL Server verknüpfen. In SQL Server stellt eine [externe Tabelle](../../t-sql/statements/create-external-table-transact-sql.md) oder [externe Datenquelle](../../t-sql/statements/create-external-data-source-transact-sql.md) die Verbindung mit Hadoop bereit.

![PolyBase logical](../../relational-databases/polybase/media/polybase-logical.png "PolyBase logical")

PolyBase überträgt einige Berechnungen per Push an den Hadoop-Knoten, um die Abfrage insgesamt zu optimieren. Der externe PolyBase-Zugriff ist jedoch nicht auf Hadoop beschränkt. Andere unstrukturierte nicht relationale Tabellen werden ebenfalls unterstützt, z.B. durch Trennzeichen getrennte Textdateien.

> [!TIP]
> Mit SQL Server 2019 CTP 2.0 werden neue Connectors für PolyBase, einschließlich SQL Server, Oracle, Teradata und MongoDB eingeführt. Weitere Informationen finden Sie in der [PolyBase-Dokumentation für SQL Server 2019 CTP 2.0](polybase-guide.md?view=sql-server-ver15).

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

PolyBase ermöglicht Ihrer SQL Server-Instanz das Verarbeiten von Transact-SQL-Abfragen, die Daten aus externen Datenquellen lesen. SQL Server 2016 und höhere Versionen können auf externe Daten in Hadoop und Azure Blob Storage zugreifen. Ab SQL Server 2019 CTP 2.0 können Sie PolyBase verwenden, um auf externe Daten in [SQL Server](polybase-configure-sql-server.md), [Oracle](polybase-configure-oracle.md), [Teradata](polybase-configure-teradata.md) und [MongoDB](polybase-configure-mongodb.md) zuzugreifen.

Die gleichen Abfragen, die auf externe Daten zugreifen, können für relationale Tabellen in Ihrer SQL Server-Instanz verwendet werden. Dadurch können Sie Daten aus externen Quellen mit wertvollen relationalen Daten in Ihrer Datenbank kombinieren. In SQL Server stellt eine [externe Tabelle](../../t-sql/statements/create-external-table-transact-sql.md) oder [externe Datenquelle](../../t-sql/statements/create-external-data-source-transact-sql.md) die Verbindung mit Hadoop bereit.

PolyBase überträgt einige Berechnungen per Push an den Hadoop-Knoten, um die Abfrage insgesamt zu optimieren. Der externe PolyBase-Zugriff ist jedoch nicht auf Hadoop beschränkt. Andere unstrukturierte nicht relationale Tabellen werden ebenfalls unterstützt, z.B. durch Trennzeichen getrennte Textdateien.

::: moniker-end

### <a name="supported-sql-products-and-services"></a>Unterstützte SQL-Produkte und -Dienste

PolyBase bietet dieselben Funktionen für die folgenden SQL-Produkte von Microsoft:

- SQL Server 2016 und höhere Versionen (nur unter Windows)
- Analytics Platform System (ehemals Parallel Data Warehouse)
- Azure SQL Data Warehouse

### <a name="azure-integration"></a>Azure-Integration

Durch die zugrunde liegende Unterstützung von PolyBase können T-SQL-Abfragen außerdem Daten aus Azure Blob Storage importieren und exportieren. PolyBase ermöglicht Azure SQL Data Warehouse zudem das Importieren und Exportieren von Daten aus Azure Data Lake Store und aus Azure Blob Storage.

## <a name="why-use-polybase"></a>Gründe für die Verwendung von PolyBase

In der Vergangenheit war es schwieriger, Ihre SQL Server-Daten mit externen Daten zu verknüpfen. Ihnen standen die beiden folgenden unpraktischen Optionen zur Auswahl:

- Übertragen der Hälfte Ihrer Daten, damit all Ihre Daten in dem einen oder in dem anderen Format vorliegen.
- Abfragen beider Datenquellen und Schreiben benutzerdefinierter Abfragelogik zum Verknüpfen und Integrieren der Daten auf Clientebene.

Mit PolyBase vermeiden Sie diese beiden Optionen, indem Sie die Daten mithilfe von T-SQL verknüpfen.

Einfach ausgedrückt: Mit PolyBase müssen Sie keine zusätzliche Software in Ihrer Hadoop-Umgebung installieren. Sie fragen externe Daten anhand der gleichen T-SQL-Syntax ab, die auch zum Abfragen einer Datenbanktabelle verwendet wird. Alle von PolyBase implementierten Unterstützungsaktionen werden transparent durchgeführt. Der Abfrageautor benötigt keine Hadoop-Kenntnisse.

### <a name="polybase-uses"></a>Verwendungszwecke von PolyBase

PolyBase ermöglicht die folgenden Szenarios in SQL Server:

- **Abfragen von in Hadoop gespeicherten Daten von SQL Server oder PDW.** Benutzer speichern Daten in kostengünstigen verteilten und skalierbaren Systemen, wie z.B. Hadoop. PolyBase vereinfacht die Abfrage der Daten mithilfe von T-SQL.

- **Abfragen von in Azure Blob Storage gespeicherten Daten.** Ein Azure-Blobspeicher ist eine bequeme Möglichkeit, Daten zu speichern, die von Azure-Diensten verwendet werden.  PolyBase vereinfacht den Zugriff auf die Daten mithilfe von T-SQL.

- **Importieren von Daten aus Hadoop, Azure Blob Storage oder Azure Data Lake Store.** Profitieren Sie von der Geschwindigkeit der Columnstore-Technologie und den Analysefunktionen von Microsoft SQL, indem Sie Daten aus Hadoop, Azure Blob Storage oder Azure Data Lake Store in relationale Tabellen importieren. Sie benötigen keine separaten ETL-Funktionen und kein Importtool.

- **Exportieren von Daten in Hadoop, Azure-Blobspeicher oder Azure Data Lake Store.** Archivieren Sie Daten in Hadoop, Azure-Blobspeichern oder Azure Data Lake Store, um kostengünstigen Speicherplatz zu nutzen und Daten für einfachen Zugriff online zu halten.

- **Integrieren in BI-Tools.** Verwenden Sie PolyBase zusammen mit den Business Intelligence- und Analysfunktionen von Microsoft, oder verwenden Sie beliebige Drittanbietertools, die mit SQL Server kompatibel sind.

## <a name="performance"></a>Leistung

- **Übertragen von Berechnungen an Hadoop.** Der Abfrageoptimierer trifft eine kostenbasierte Entscheidung darüber, ob die Berechnung an Hadoop übertragen wird, um die Abfrageleistung zu verbessern.  Für diese kostenbasierte Entscheidung verwendet der Optimierer Statistiken in externen Tabellen. Bei der Übertragung der Berechnung werden MapReduce-Aufträge erstellt und die verteilten Berechnungsressourcen von Hadoop genutzt.

- **Skalieren von Berechnungsressourcen.** Um die Abfrageleistung zu verbessern, können Sie [PolyBase-Erweiterungsgruppen](../../relational-databases/polybase/polybase-scale-out-groups.md)von SQL Server verwenden. Die ermöglicht eine parallele Datenübertragung zwischen SQL Server-Instanzen und Hadoop-Knoten und fügt Berechnungsressourcen für die Verarbeitung der externen Daten hinzu.

<!--SQL Server 2016/2017-->
::: moniker range="=sql-server-2016||=sql-server-2017"

## <a name="next-steps"></a>Nächste Schritte

Bevor Sie PolyBase verwenden können, müssen Sie [das PolyBase-Feature installieren](polybase-installation.md). Befolgen Sie dann je nach Datenquelle die Anweisungen in einem der folgenden Konfigurationshandbücher:

- [Hadoop](polybase-configure-hadoop.md)
- [Azure Blob Storage](polybase-configure-azure-blob-storage.md)

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-linux-ver15||>= sql-server-ver15||=sqlallproducts-allversions"

## <a name="next-steps"></a>Nächste Schritte

Bevor Sie PolyBase verwenden können, müssen Sie [das PolyBase-Feature installieren](polybase-installation.md). Befolgen Sie dann je nach Datenquelle die Anweisungen in einem der folgenden Konfigurationshandbücher:
- [Hadoop](polybase-configure-hadoop.md)
- [Azure Blob Storage](polybase-configure-azure-blob-storage.md)
- [SQL Server](polybase-configure-sql-server.md)
- [Oracle](polybase-configure-oracle.md)
- [Teradata](polybase-configure-teradata.md)
- [MongoDB](polybase-configure-mongodb.md)
- [Generische ODBC-Typen](../../relational-databases/polybase/polybase-installation.md)

::: moniker-end
