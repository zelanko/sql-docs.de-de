---
title: "\"Wideworldimporters\" Generieren von Daten - SQL-Beispieldatenbank | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b0fd90b553aaefad61d9285f8630650b2b38763d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810538"
---
# <a name="wideworldimporters-data-generation"></a>Datengenerierung "wideworldimporters"
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Die Versionen der Datenbanken "wideworldimporters" und "wideworldimportersdw" müssen Daten aus dem 1. Januar 2013, bis zu dem Tag, den die Datenbanken generiert wurden.

Wenn Sie diese Beispieldatenbanken verwenden, empfiehlt es sich, neuere Beispieldaten.

## <a name="data-generation-in-wideworldimporters"></a>Datengenerierung im "wideworldimporters"

So generieren Sie Beispieldaten bis zum aktuellen Datum

1. Wenn Sie dies nicht getan haben, installieren Sie eine saubere Version der Datenbank "wideworldimporters". Installationsanweisungen finden Sie unter [Installation und Konfiguration](wide-world-importers-oltp-install-configure.md).
2. Führen Sie die folgende Anweisung aus, in der Datenbank:

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    Diese Anweisung fügt Beispiel Sales und Kaufdaten für die Datenbank bis zum aktuellen Datum. Es zeigt den Status der Data Generation an, nach Tag. Datengenerierung dauert ungefähr 10 Minuten für jedes Jahr, die Daten benötigt. Aufgrund der zufälligen Faktor bei der die datengenerierung gibt es einige Unterschiede in den Daten, die zwischen den Ausführungen generiert wird.

    Ändern Sie zum Erhöhen oder verringern die Menge der Daten für Aufträge pro Tag generiert, den Wert für den Parameter `@AverageNumberOfCustomerOrdersPerDay`. Verwenden Sie die Parameter `@SaturdayPercentageOfNormalWorkDay` und `@SundayPercentageOfNormalWorkDay` Sie das Auftragsvolumen für Wochenendtage zu ermitteln.

## <a name="import-generated-data-in-wideworldimportersdw"></a>Generiert von Daten im "wideworldimportersdw"

So importieren Sie Beispieldaten, bis das aktuelle Datum in der WideWorldImportersDW OLAP-Datenbank

1. Führen Sie die Generierungslogik Daten in der WideWorldImporters-OLTP-Datenbank mithilfe der Schritte im vorherigen Abschnitt.
2. Wenn Sie dies noch nicht getan haben, installieren Sie eine saubere Version der Datenbank "wideworldimportersdw" aus. Installationsanweisungen finden Sie unter [Installation und Konfiguration](wide-world-importers-oltp-install-configure.md).
3. Neue Ausgangswerte zuzuweisen Sie und die OLAP-Datenbank durch Ausführen der folgenden Anweisung in der Datenbank:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Führen Sie die *tägliche ETL.ispac* SQL Server Integration Services-Paket, um die Daten in der OLAP-Datenbank importieren. Gewusst wie: Ausführen den ETL-Auftrag finden Sie unter [WideWorldImporters-ETL-Workflow](wide-world-importers-perform-etl.md).

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>Generieren von Daten in "wideworldimportersdw" für Leistungstests

"Wideworldimportersdw" kann die Größe der Daten für das Testen der Leistung nach dem Zufallsprinzip erhöhen. Beispielsweise können sie die Größe der Daten für die Verwendung mit gruppierten columnstore-Indizierung erhöhen.

Ist eine der Herausforderungen, die Größe des Downloads klein genug ist, jedoch gleichzeitig Groß herunterladen genug, um SQL Server-Leistung-Funktionen zeigen einfach zu halten. Beispielsweise werden erhebliche Vorteile für columnstore-Indizes erreicht, nur bei der Arbeit mit einer größeren Anzahl von Zeilen. 

Sie können die `Application.Configuration_PopulateLargeSaleTable` Verfahren zum Erhöhen der Anzahl der Zeilen in der `Fact.Sale` Tabelle. Die Zeilen eingefügt werden, in das Kalenderjahr 2012, um zu vermeiden, Kollision mit vorhandenen World Wide Importers-Daten, die am 1. Januar 2013 beginnt.

### <a name="procedure-details"></a>Verfahren

#### <a name="name"></a>Name

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Parameter

  `@EstimatedRowsFor2012` **Bigint** (mit einem Standardwert von 12000000)

#### <a name="result"></a>Ergebnis

Etwa die erforderliche Anzahl von Zeilen werden eingefügt, in der `Fact.Sale` -Tabelle in das Jahr 2012. Die Prozedur beschränkt die Standardanzahl der Anzahl der Zeilen auf 50.000 pro Tag. Sie können diese Einschränkung ändern, aber die Beschränkung auf Ihnen hilft, unbeabsichtigte Overinflations der Tabelle.

Das Verfahren gilt auch gruppierten columnstore-Indizierung, wenn es bereits angewendet wurde.
