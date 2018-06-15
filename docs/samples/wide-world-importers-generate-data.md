---
title: "\"Wideworldimporters\" Generieren von Daten - SQL-Beispieldatenbank | Microsoft Docs"
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ace1f771ef3a77a6f7db0072442affe181d7872
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467816"
---
# <a name="wideworldimporters-data-generation"></a>"Wideworldimporters" Datengenerierungsplan
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Die Versionen der Datenbanken "wideworldimporters" und WideWorldImportersDW haben Daten ab dem 1. Januar 2013 bis zu den Tag, den die Datenbanken generiert wurden.

Wenn Sie diese Beispieldatenbanken verwenden, empfiehlt es sich, neuere Sample-Daten enthalten.

## <a name="data-generation-in-wideworldimporters"></a>Generieren von Daten in "wideworldimporters"

Zum Generieren von Beispieldaten bis zum aktuellen Datum:

1. Wenn Sie dies geschehen ist, installieren Sie eine saubere Version der Datenbank "wideworldimporters". Installationsanweisungen finden Sie unter [Installation und Konfiguration](wide-world-importers-oltp-install-configure.md).
2. Führen Sie die folgende Anweisung in der Datenbank an:

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    Diese Anweisung fügt Beispiel Sales und die Bestellung-Daten in die Datenbank bis zum aktuellen Datum. Es zeigt den Status der datengenerierung nach Tag. Der datengenerierung kann einmal im Jahr bis zu 10 Minuten dauern, die Daten benötigt. Aufgrund einer Zufallsfaktor in die datengenerierung gibt es einige Unterschiede in den Daten, die zwischen den Ausführungen generiert wird.

    Erhöhen oder verringern die Menge der Daten für Aufträge pro Tag generiert, ändern Sie den Wert für den Parameter `@AverageNumberOfCustomerOrdersPerDay`. Verwenden Sie die Parameter `@SaturdayPercentageOfNormalWorkDay` und `@SundayPercentageOfNormalWorkDay` , das Auftragsvolumen für Wochenendtage zu bestimmen.

## <a name="import-generated-data-in-wideworldimportersdw"></a>Generiert Daten in WideWorldImportersDW

Beispieldaten, bis das aktuelle Datum in der WideWorldImportersDW OLAP-Datenbank zu importieren:

1. Führen Sie die Logik der zur Generierung in der WideWorldImporters OLTP-Datenbank mithilfe der Schritte im vorherigen Abschnitt.
2. Wenn Sie dies noch nicht getan haben, installieren Sie eine saubere Version der Datenbank WideWorldImportersDW. Installationsanweisungen finden Sie unter [Installation und Konfiguration](wide-world-importers-oltp-install-configure.md).
3. Als Ausgangswert für die OLAP-Datenbank durch Ausführen der folgenden Anweisung in der Datenbank:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Führen Sie die *tägliche ETL.ispac* SQL Server Integration Services-Paket, um die Daten in der OLAP-Datenbank importieren. Weitere Informationen zum Ausführen des ETL-Auftrags finden Sie unter [WideWorldImporters ETL-Workflows](wide-world-importers-perform-etl.md).

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>Generieren von Daten in WideWorldImportersDW aber für Leistungstests

WideWorldImportersDW kann nach dem Zufallsprinzip Daten aber für Leistungstests vergrößern. Beispielsweise können sie Daten für die Verwendung mit gruppierten columnstore-Index vergrößern.

Eine der Herausforderungen ist die Größe des Downloads klein genug für die lang herunterladen genug, um SQL Server-Leistung-Funktionen veranschaulichen einfach zu halten. Beispielsweise werden bedeutende Vorteile für columnstore-Indizes erzielt nur bei der Arbeit mit einer größeren Anzahl von Zeilen. 

Sie können die `Application.Configuration_PopulateLargeSaleTable` Verfahren zum Erhöhen der Anzahl der Zeilen in der `Fact.Sale` Tabelle. Die Zeilen eingefügt werden, in das Kalenderjahr 2012, um zu vermeiden, implementierungsgrenzen vorhandenen Wide World Importers-Daten, die am 1. Januar 2013 beginnt.

### <a name="procedure-details"></a>Prozedur-details

#### <a name="name"></a>Name

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Parameter

  `@EstimatedRowsFor2012` **"bigint"** (hat den Standardwert 12000000)

#### <a name="result"></a>Ergebnis

In etwa die erforderliche Anzahl von Zeilen eingefügt werden die `Fact.Sale` Tabelle im Jahr 2012. Die Prozedur beschränkt die Standardanzahl der Anzahl der Zeilen auf 50.000 pro Tag. Sie können diese Einschränkung ändern, aber die Einschränkung können Sie die versehentliche Overinflations der Tabelle zu vermeiden.

Das Verfahren gilt auch clustered Columnstore indizieren, wenn er bereits angewendet wurde.
