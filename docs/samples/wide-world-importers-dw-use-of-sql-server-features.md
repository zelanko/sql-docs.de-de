---
title: 'WideWorldImporters-OLAP-Datenbank: Verwenden von SQL Server | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7c3158def05148941105867f24205b199e6c6dba
ms.sourcegitcommit: 89983916c39b1c3ecf340de6a4febb2ed33129e4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "36964262"
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>"Wideworldimportersdw" Verwenden von SQL Server-Features und Funktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
"Wideworldimportersdw" dient, viele der wichtigsten Features von SQL Server zu veranschaulichen, die für Data warehousing und Analysen geeignet sind. Im folgenden finden eine Liste von SQL Server-Features und Funktionen und eine Beschreibung der, wie sie in "wideworldimportersdw" verwendet werden.

## <a name="polybase"></a>PolyBase

[Gilt für SQL Server (2016 und höher)]

PolyBase wird zum Kombinieren von Verkaufsinformationen für "wideworldimportersdw" mit einem öffentlichen DataSet zu demografischen Daten, um zu verstehen, welche Städten für eine weitere Erweiterung der Verkauf von Interesse sein können.

Um die Verwendung von PolyBase in der Beispieldatenbank zu aktivieren, stellen Sie sicher, dass es installiert ist, und führen Sie die folgende gespeicherte Prozedur in der Datenbank:

    EXEC [Application].[Configuration_ApplyPolybase]

Hiermit wird eine externe Tabelle `dbo.CityPopulationStatistics` , die auf einem öffentlichen DataSet, die Bevölkerungsdaten für Städte in den Vereinigten Staaten, gehostet in Azure Blob Storage verweist. Es wird empfohlen, den Code in der gespeicherten Prozedur den Konfigurationsprozess zu überprüfen. Wenn Sie Ihre eigenen Daten im Azure-Blob-Speicher zu hosten, und bewahren Sie sie vor den allgemeinen öffentlichen Zugriff geschützt werden sollen, müssen Sie zusätzliche Konfigurationsschritte ausführt. Die folgende Abfrage gibt die Daten von der Festlegung der externen Daten:

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

Um zu verstehen, welche Städten für eine weitere Erweiterung von Interesse sein können, die folgende Abfrage untersucht die Wachstumsrate von Städten und gibt die ersten 100 größten Städte mit erheblicher Anstieg und Wide World Importers hat, in denen keine Verkäufe präsent. Die Abfrage enthält einen Join zwischen der Remotetabelle `dbo.CityPopulationStatistics` und die lokale Tabelle `Dimension.City`, und einen Filter, die im Zusammenhang mit der lokalen Tabelle `Fact.Sales`.

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

Gruppierte columnstore-Indizes (CCI) werden zum alle die Faktentabellen reduzieren den Speicherplatzbedarf und abfrageleistung zu verbessern. Mit der Verwendung von CCI verwendet der Basis Speicher für die Faktentabellen Spalte-Komprimierung.

Nicht gruppierte Indizes werden zusätzlich zu den gruppierten columnstore-Index verwendet, um die primary key- und foreign Key-Einschränkungen zu vereinfachen. Diese Einschränkungen wurden hinzugefügt, aus einer Fülle von Vorsicht – ETL-Prozess die Datenquellen aus der Datenbank "wideworldimporters", mit Einschränkungen zum Erzwingen der Integrität. Entfernen von primären und foreign Key-Einschränkungen und deren unterstützende Indizes verringert sich der Speicherbedarf der Faktentabellen.

**Größe der Daten**

Die-Beispieldatenbank verfügt über eingeschränkte Größe der Daten, um das Herunterladen und Installieren des Beispiels zu erleichtern. Um die tatsächliche Leistungsvorteile von columnstore-Indizes zu sehen, möchten allerdings würde ein größeren Datasets verwenden.

Sie können die folgende Anweisung zum Erhöhen der Größe der Ausführen der `Fact.Sales` Tabelle durch Einfügen von einem anderen 12 Millionen Zeilen mit Beispieldaten. Diese Zeilen werden alle für das Jahr 2012 eingefügt, keine Beeinträchtigung durch die ETL-Prozesse sind.

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

Diese Anweisung dauert ca. fünf Minuten ausgeführt. Um mehr als 12 Millionen Zeilen einzufügen, übergeben Sie die gewünschte Anzahl von Zeilen, die als Parameter dieser gespeicherten Prozedur eingefügt.

Um die abfrageleistung mit und ohne Columnstore zu vergleichen, können Sie löschen und/oder erstellen Sie den gruppierten columnstore-Index neu.

So löschen Sie den Index:

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

Um erneut zu erstellen:

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>Partitionierung

(Vollständige Version des Beispiels)

Größe der Daten in einem Data Warehouse kann sehr groß werden. Aus diesem Grund ist es die bewährte Methode, die Verwendung der Partitionierung zum Verwalten der Speicherung von die großen Tabellen in der Datenbank.

Alle größeren Faktentabellen werden nach Jahr partitioniert. Die einzige Ausnahme ist `Fact.Stock Holdings`, dies ist kein datumsbasierte und verfügt über nur einen eingeschränkten Datenumfang verglichen mit den anderen Faktentabellen.

Wird für alle partitionierten Tabellen verwendete Partitionsfunktion `PF_Date`, und das Partitionsschema verwendeten `PS_Date`.

## <a name="in-memory-oltp"></a>In-Memory OLTP

(Vollständige Version des Beispiels)

"Wideworldimportersdw" verwendet den speicheroptimierten SCHEMA_ONLY-Tabellen für den staging-Tabellen. Alle `Integration.` * `_Staging` Tabellen sind speicheroptimierten SCHEMA_ONLY-Tabellen.

Der Vorteil der SCHEMA_ONLY-Tabellen ist, dass sie nicht angemeldet sind und Zugriff auf die Festplatte ist nicht erforderlich. Dies verbessert die Leistung der ETL-Prozess. Da diese Tabellen nicht angemeldet sind, werden Sie in ihren Inhalt verloren, wenn ein Fehler auftritt. Allerdings ist die Datenquelle noch verfügbar ist, damit die ETL-Prozesse einfach neu gestartet werden kann, wenn ein Fehler auftritt.
