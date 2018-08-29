---
title: WideWorldImporters OLAP-Datenbank-Katalog – SQL | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: cbdcbe160e585fc1d5dfc30c51f511f32d4a0be9
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43104664"
---
# <a name="wideworldimportersdw-database-catalog"></a>Datenbankkatalog "wideworldimportersdw"
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Erklärungen zu den Schemas, Tabellen und gespeicherten Prozeduren in der Datenbank "wideworldimportersdw". 

Die Datenbank "wideworldimportersdw" wird für Datawarehousing und analytische Verarbeitung verwendet. Die Transaktionsdaten zu und Verkäufe in der Datenbank "wideworldimporters" generiert und in die Datenbank mit "wideworldimportersdw" geladen ist eine **tägliche ETL-Prozess**.

Die Daten in "wideworldimportersdw" spiegelt daher die Daten in "wideworldimporters", aber die Tabellen sind unterschiedlich organisiert. "Wideworldimportersdw" wird verwendet, während "wideworldimporters" ein herkömmlichen, normalisiertes Schema verfügt, die [Sternschema](https://wikipedia.org/wiki/Star_schema) Ansatz für die Tabellen-Entwurf. Neben den Tabellen Fakten- und Dimensionstabellen enthält die Datenbank eine Anzahl von Stagingtabellen, die verwendet werden, in der ETL-Prozess.

## <a name="schemas"></a>Schemas

Die verschiedenen Arten von Tabellen sind in drei Schemas organisiert.

|Schema|Description|
|-----------------------------|---------------------|
|Dimension|Dimensionstabellen.|
|Fakt|Faktentabellen.|  
|Integration|Staging-Tabellen und andere Objekte, die für ETL erforderlich sind.|  

## <a name="tables"></a>Tabellen

Die Tabellen Dimensions- und Faktentabellen sind unten aufgeführt. Die Tabellen im Schema Integration werden nur für die ETL-Prozesse verwendet und sind nicht aufgeführt.

### <a name="dimension-tables"></a>Dimensionstabellen

"Wideworldimportersdw" hat die folgenden Dimensionstabellen. Die Beschreibung enthält die Beziehung mit den Quelltabellen in der Datenbank "wideworldimporters".

|Tabelle|Quelltabellen|
|-----------------------------|---------------------|
|Ort|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|date|Neue Tabelle mit Informationen zu den Datumsangaben, einschließlich der Geschäftsjahr (basierend auf dem 1. November für Geschäftsjahr starten).|
|Employee|`Application.People`. installiert haben.|
|StockItem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|Lieferanten|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods`. installiert haben.|
|TransactionType|`Application.TransactionTypes`. installiert haben.|

### <a name="fact-tables"></a>Faktentabellen

"Wideworldimportersdw" hat die folgenden Faktentabellen. Die Beschreibung enthält die Beziehung mit den Quelltabellen in die Datenbank "wideworldimporters" als auch die Klassen von Analytics/berichterstellung Abfragen, die einzelnen Faktentabellen in der Regel mit verwendet wird.

|Tabelle|Quelltabellen|Beispiel-Analysen|
|-----------------------------|---------------------|---------------------|
|Order|`Sales.Orders` und `Sales.OrderLines`|Sales Personen "," Auswahl/Packer-Produktivität, und auf Zeit, um Aufträge auszuwählen. Darüber hinaus niedrige vordefinierte Situationen zu Bestellungen zurück.|
|Ausverkauf|`Sales.Invoices` und `Sales.InvoiceLines`|Sales Datumsangaben, Lieferdaten, Rentabilität im Laufe der Zeit, Profitabilität nach Vertriebsmitarbeiter.|
|Kauf|`Purchasing.PurchaseOrderLines`|Erwartete und tatsächliche Lieferzeiten|
|Transaction|`Sales.CustomerTransactions` und `Purchasing.SupplierTransactions`|Messen der Problem Datumsangaben im Vergleich zur Finalisierung Datumsangaben und Mengen.|
|Datenverschiebung|`Warehouse.StockTransactions`|Bewegungen, die im Laufe der Zeit.|
|Aktien gehalten|`Warehouse.StockItemHoldings`|Verfügbare Lagerbestände und Wert.|

## <a name="stored-procedures"></a>Gespeicherte Prozeduren

Die gespeicherten Prozeduren werden in erster Linie für die ETL-Prozesse und Konfigurationszwecken verwendet.

Alle Erweiterungen des Beispiels werden empfohlen, mit der `Reports` Schema für Reporting Services-Berichten und die `PowerBI` Schema für den Zugang zu Power BI.

### <a name="application-schema"></a>Anwendungsschema

Diese Prozeduren werden verwendet, zum Konfigurieren des Beispiels. Sie werden verwendet, zum Anwenden von Funktionen der Enterprise Edition auf die standard Edition-Version des Beispiels, PolyBase hinzufügen und neue Ausgangswerte zuzuweisen und ETL.

|Verfahren|Zweck|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|Wendet die Partitionierung und columnstore-Indizes für Tabellen.|
|Configuration_ConfigureForEnterpriseEdition|Wendet die Partitionierung, Columnstore-Indizierung und in-Memory.|
|Configuration_EnableInMemory|Ersetzt die Stagingtabellen für die Integration mit einer speicheroptimierten SCHEMA_ONLY-Tabellen, um ETL-Leistung zu verbessern.|
|Configuration_ApplyPolybase|Konfiguriert eine externe Datenquelle, Dateiformat und Tabelle.|
|Configuration_PopulateLargeSaleTable|Enterprise Edition-Änderungen werden übernommen, und dann eine größere Menge an Daten für das Kalenderjahr 2012, als weiterer Verlauf füllt.|
|Configuration_ReseedETL|Vorhandene Daten entfernt, und die ETL-Seeds Neustart. Dadurch können für die OLAP-Datenbank für das streckungsschema an aktualisierten Zeilen in der OLTP-Datenbank übereinstimmen.|

### <a name="integration-schema"></a>Integration von Schemas

In der ETL-Prozess verwendete Prozeduren werden in den folgenden Kategorien:
- Hilfsprozeduren für das ETL-Paket – alle Get * Verfahren.
- Prozeduren, die von der ETL-Pakets verwendet werden, für die Migration werden Daten in die Data Warehouse-Tabellen - alle migrieren * Prozeduren bereitgestellt.
- `PopulateDateDimensionForYear` : Nimmt ein Jahr und stellt sicher, dass alle Datumsangaben für dieses Jahr in aufgefüllt werden die `Dimension.Date` Tabelle.

### <a name="sequences-schema"></a>Schema für Sequenzen

Vor, um die Sequenzen in der Datenbank zu konfigurieren.

|Verfahren|Zweck|
|-----------------------------|---------------------|
|ReseedAllSequences|Ruft die Prozedur `ReseedSequenceBeyondTableValue` für alle folgen.|
|ReseedSequenceBeyondTableValue|Wird verwendet, um den nächsten Sequenzwert über den Wert in einer beliebigen Tabelle neu zu positionieren, die dieselbe Tasksequenz verwendet. (Z. B. eine `DBCC CHECKIDENT` für Identität Spalten entspricht, für die Sequenzen, aber auf potenziell mehrere Tabellen.)|
