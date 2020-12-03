---
description: Weitergabeberechnungen in PolyBase
title: Weitergabeberechnungen in PolyBase | Microsoft-Dokumentation
dexcription: Enable pushdown computation to improve performance of queries on your Hadoop cluster. You can select a subset of rows/columns in an external table for pushdown.
ms.date: 11/17/2020
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
monikerRange: '>= sql-server-2016 || =sqlallproducts-allversions'
ms.openlocfilehash: 59ff1e7807a8bdd8427e3b902bf53c111d52c7b7
ms.sourcegitcommit: 4c3949f620d09529658a2172d00bfe37aeb1a387
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "96127843"
---
# <a name="pushdown-computations-in-polybase"></a>Weitergabeberechnungen in PolyBase

[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

Weitergabeberechnungen verbessern die Leistung von Abfragen in externen Datenquellen. Seit SQL Server 2016 sind Weitergabeberechnungen für externe Hadoop-Datenquellen verfügbar. In SQL Server 2019 wurden Weitergabeberechnungen für andere Arten von externen Datenquellen eingeführt.

## <a name="enable-pushdown-computation"></a> Aktivieren der Weitergabeberechnung

Die folgenden Artikel enthalten Informationen zum Konfigurieren von Weitergabeberechnungen für bestimmte Typen von externen Datenquellen:

- [Aktivieren der Weitergabeberechnung in Hadoop](polybase-configure-hadoop.md#pushdown)
- [Konfigurieren von PolyBase für den Zugriff auf externe Daten in Oracle](polybase-configure-oracle.md)
- [Konfigurieren von PolyBase für den Zugriff auf externe Daten in Teradata](polybase-configure-teradata.md)
- [Konfigurieren von PolyBase für den Zugriff auf externe Daten in MongoDB](polybase-configure-mongodb.md)
- [Konfigurieren von PolyBase für den Zugriff auf externe Daten mit generischen ODBC-Typen](polybase-configure-odbc-generic.md)
- [Konfigurieren von PolyBase für den Zugriff auf externe Daten in SQL Server](polybase-configure-sql-server.md)

## <a name="select-a-subset-of-rows"></a>Auswählen einer Teilmenge von Zeilen

Verwenden Sie die Prädikatweitergabe zum Verbessern der Leistung für eine Abfrage, die eine Teilmenge von Zeilen aus einer externen Tabelle auswählt.

In diesem Beispiel initiiert SQL Server 2016 einen map-reduce-Auftrag zum Abrufen der Zeilen, die dem Prädikat `customer.account_balance < 200000` auf Hadoop entsprechen. Da die Abfrage nicht erfolgreich abschließen kann, ohne alle Zeilen der Tabelle zu scannen, werden nur die Zeilen, die den Prädikatskriterien entsprechen, in SQL Server kopiert. Dies spart Zeit und erfordert weniger temporären Speicherplatz, wenn die Anzahl der Debitorensalden < 200000 im Vergleich mit der Anzahl der Kunden mit Kontensalden >= 200000 klein ist.

```sql
SELECT * FROM customer WHERE customer.account_balance < 200000
SELECT * FROM SensorData WHERE Speed > 65;  
```

### <a name="select-a-subset-of-columns"></a>Auswählen einer Teilmenge von Spalten

Verwenden Sie die Prädikatweitergabe zum Verbessern der Leistung für eine Abfrage, die eine Teilmenge von Spalten aus einer externen Tabelle auswählt.

In dieser Abfrage initiiert SQL Server einen MapReduce-Auftrag, um die durch Trennzeichen getrennte Hadoop-Textdatei vorab zu verarbeiten, sodass nur die Daten der zwei Spalten „customer.name“ und „customer.zip_code“ in SQL Server kopiert werden.

```sql
SELECT customer.name, customer.zip_code
FROM customer
WHERE customer.account_balance < 200000
```

### <a name="pushdown-for-basic-expressions-and-operators"></a>Weitergabe für grundlegende Ausdrücke und Operatoren

SQL Server erlaubt die folgenden grundlegenden Ausdrücke und Operatoren für Prädikatweitergabe.

- Binäre Vergleichsoperatoren (`<`, `>`, `=`, `!=`, `<>`, `>=`, `<=`) für die Zahlen-, Datums- und Zeitwerte.
- Arithmetische Operatoren (`+`, `-`, `*`, `/`, `%`)
- Logische Operatoren (`AND`, `OR`)
- Unäre Operatoren (`NOT`, `IS NULL`, `IS NOT NULL`)

Die Operatoren `BETWEEN`, `NOT`, `IN` und `LIKE` werden möglicherweise weitergegeben. Das aktuelle Verhalten hängt davon ab, wie der Abfrageoptimierer die Operatorausdrücke als eine Reihe von Anweisungen neu schreibt, die grundlegende relationale Operatoren verwenden.

Die Abfrage in diesem Beispiel verfügt über mehrere Prädikate, die an Hadoop weitergegeben werden können. SQL Server kann map-reduce-Aufträge an Hadoop weitergeben, um das Prädikat `customer.account_balance <= 200000` auszuführen. Der Ausdruck `BETWEEN 92656 AND 92677` besteht auch aus binären und logischen Operationen, die an Hadoop weitergegeben werden können. Das logische **AND** in `customer.account_balance AND customer.zipcode` ist ein finaler Ausdruck.

Mit dieser Kombination von Prädikaten können also die map-reduce-Aufträge alle Bedingungen der WHERE-Klausel vollständig bearbeiten. Nur die Daten, die die Kriterien von `SELECT` erfüllen, werden in SQL Server zurückkopiert.

```sql
SELECT * FROM customer 
WHERE customer.account_balance <= 200000 
    AND customer.zipcode BETWEEN 92656 AND 92677
```

## <a name="examples"></a>Beispiele

### <a name="force-pushdown"></a>Weitergabe erzwingen

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (FORCE EXTERNALPUSHDOWN);
```

### <a name="disable-pushdown"></a>Weitergabe deaktivieren

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (DISABLE EXTERNALPUSHDOWN);
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie im [PolyBase-Leitfaden](polybase-guide.md).
