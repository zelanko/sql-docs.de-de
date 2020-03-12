---
title: Wichtige Features in der DW-Datenbank wideworldimporters
description: Erfahren Sie, wie die Datenbank "wideworldimportersdw" wichtige Features von SQL Server präsentiert, die für Data Warehousing und Analysen geeignet sind.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: 431ca4762b15003f49a5145eb603b7508f2d6844
ms.sourcegitcommit: 59c09dbe29882cbed539229a9bc1de381a5a4471
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79112423"
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>Wideworldimportersdw Verwendung von SQL Server Features und Funktionen
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Wideworldimportersdw ist so konzipiert, dass viele der wichtigsten Features von SQL Server vorgestellt werden, die für Data Warehousing und Analysen geeignet sind. Im folgenden finden Sie eine Liste der SQL Server Features und Funktionen sowie eine Beschreibung der Verwendung in wideworldimportersdw.

## <a name="polybase"></a>PolyBase

[Gilt für SQL Server (2016 und höher)]

Polybase wird zum Kombinieren von Umsatz Informationen aus wideworldimportersdw mit einem öffentlichen DataSet über Demographics verwendet, um zu verstehen, welche Städte für eine weitere Vertriebs Erweiterung von Interesse sein könnten.

Um die Verwendung von polybase in der-Beispieldatenbank zu aktivieren, stellen Sie sicher, dass Sie installiert ist, und führen Sie die folgende gespeicherte Prozedur in der-Datenbank aus:

    EXEC [Application].[Configuration_ApplyPolyBase]

Dadurch wird eine externe Tabelle `dbo.CityPopulationStatistics` erstellt, die auf ein öffentliches DataSet verweist, das auffüllungs Daten für Städte in der USA enthält, die in Azure BLOB Storage gehostet werden. Es wird empfohlen, den Code in der gespeicherten Prozedur zu überprüfen, um den Konfigurationsprozess zu verstehen. Wenn Sie Ihre eigenen Daten in Azure BLOB Storage hosten und Sie vor dem allgemeinen öffentlichen Zugriff schützen möchten, müssen Sie zusätzliche Konfigurationsschritte ausführen. Die folgende Abfrage gibt die Daten aus diesem externen DataSet zurück:

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

Um zu verstehen, welche Städte für eine weitere Erweiterung von Interesse sein könnten, untersucht die folgende Abfrage die Wachstumsrate der Städte und gibt die obersten 100 größten Städte mit erheblichem Wachstum zurück, wobei Wide World-Import Programme nicht über eine Vertriebspräsenz verfügen. Die Abfrage umfasst einen Join zwischen der Remote Tabelle `dbo.CityPopulationStatistics` und der lokalen Tabelle `Dimension.City`sowie einen Filter, der die lokale Tabelle `Fact.Sales`einschließt.

    WITH PotentialCities
    AS
    (
        SELECT cps.CityName,
               cps.StateProvinceCode,
               MAX(cps.LatestRecordedPopulation) AS PopulationIn2016,
               (MAX(cps.LatestRecordedPopulation) - MIN(cps.LatestRecordedPopulation)) * 100.0
                   / MIN(cps.LatestRecordedPopulation) AS GrowthRate
        FROM dbo.CityPopulationStatistics AS cps
        WHERE cps.LatestRecordedPopulation IS NOT NULL
        AND cps.LatestRecordedPopulation <> 0
        GROUP BY cps.CityName, cps.StateProvinceCode
    ),
    InterestingCities
    AS
    (
        SELECT DISTINCT pc.CityName,
                        pc.StateProvinceCode,
                        pc.PopulationIn2016,
                        FLOOR(pc.GrowthRate) AS GrowthRate
        FROM PotentialCities AS pc
        INNER JOIN Dimension.City AS c
        ON pc.CityName = c.City
        WHERE GrowthRate > 2.0
        AND NOT EXISTS (SELECT 1 FROM Fact.Sale AS s WHERE s.[City Key] = c.[City Key])
    )
    SELECT TOP(100) CityName, StateProvinceCode, PopulationIn2016, GrowthRate
    FROM InterestingCities
    ORDER BY PopulationIn2016 DESC;

## <a name="clustered-columnstore-indexes"></a>Gruppierte Columnstore-Indizes

(Vollständige Version des Beispiels)

Gruppierte columnstore-Indizes (CCI) werden mit allen Fakten Tabellen verwendet, um den Speicherbedarf zu reduzieren und die Abfrageleistung zu verbessern. Durch die Verwendung von CCI verwendet der Basis Speicher für die Fakten Tabellen die Spalten Komprimierung.

Nicht gruppierte Indizes werden zusätzlich zum gruppierten columnstore--Index verwendet, um PRIMARY KEY-und FOREIGN KEY-Einschränkungen zu vereinfachen. Diese Einschränkungen wurden aus einer Fülle von Vorsicht hinzugefügt. der ETL-Prozess stellt die Daten aus der wideworldimporters-Datenbank dar, die Einschränkungen zum Erzwingen der Integrität haben. Wenn Sie Primary-und FOREIGN KEY-Einschränkungen und deren unterstützende Indizes entfernen, verringern Sie den Speicherplatzbedarf der Fakten Tabellen.

**Datengröße**

Die Datengröße der Beispieldatenbank ist eingeschränkt, damit das Beispiel einfach heruntergeladen und installiert werden kann. Wenn Sie jedoch die echten Leistungsvorteile von columnstore--Indizes anzeigen möchten, sollten Sie ein größeres DataSet verwenden.

Sie können die folgende Anweisung ausführen, um die Größe der `Fact.Sales` Tabelle zu vergrößern, indem Sie weitere 12 Millionen Zeilen mit Beispiel Daten einfügen. Diese Zeilen werden alle für das Jahr 2012 eingefügt, sodass der ETL-Prozess nicht beeinträchtigt wird.

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

Die Ausführung dieser Anweisung dauert ca. 5 Minuten. Wenn Sie mehr als 12 Millionen Zeilen einfügen möchten, übergeben Sie die gewünschte Anzahl von Zeilen, die als Parameter für diese gespeicherte Prozedur eingefügt werden sollen.

Zum Vergleichen der Abfrageleistung mit und ohne columnstore-können Sie den gruppierten columnstore--Index löschen und/oder neu erstellen.

So löschen Sie den Index:

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

Neu zu erstellen:

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>Partitionierung

(Vollständige Version des Beispiels)

Die Datengröße in einem Data Warehouse kann sehr groß werden. Daher empfiehlt es sich, die Partitionierung zu verwenden, um die Speicherung der großen Tabellen in der Datenbank zu verwalten.

Alle größeren Fakten Tabellen werden nach Jahr partitioniert. Die einzige Ausnahme ist `Fact.Stock Holdings`, die nicht Datums basiert ist und im Vergleich zu den anderen Fakten Tabellen eine begrenzte Datengröße aufweist.

Die Partitions Funktion, die für alle partitionierten Tabellen `PF_Date`verwendet wird, ist, und das verwendete `PS_Date`Partitionsschema ist.

## <a name="in-memory-oltp"></a>In-Memory-OLTP

(Vollständige Version des Beispiels)

Wideworldimportersdw verwendet SCHEMA_ONLY Speicher optimierte Tabellen für die Stagingtabellen. `Integration.` * Alle `_Staging` Tabellen sind SCHEMA_ONLY Speicher optimierte Tabellen.

Der Vorteil von SCHEMA_ONLY Tabellen besteht darin, dass Sie nicht protokolliert werden und keinen Datenträger Zugriff benötigen. Dies verbessert die Leistung des ETL-Prozesses. Da diese Tabellen nicht protokolliert werden, gehen Ihre Inhalte verloren, wenn ein Fehler auftritt. Die Datenquelle ist jedoch weiterhin verfügbar, sodass der ETL-Prozess bei einem Fehler einfach neu gestartet werden kann.
