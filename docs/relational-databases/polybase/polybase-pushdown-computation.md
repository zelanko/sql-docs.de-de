---
title: Weitergabeberechnungen in PolyBase | Microsoft-Dokumentation
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: aboke
monikerRange: '>= sql-server-2016 || =sqlallproducts-allversions'
ms.openlocfilehash: dcc59e6aad686cb97e4439701967dddd21182e45
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062120"
---
# <a name="pushdown-computations-in-polybase"></a>Weitergabeberechnungen in PolyBase

## <a name="dmv"></a>DMV

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Weitergabeberechnungen verbessern die Leistung von Abfragen in Ihrem Hadoop-Cluster.

## <a name="enable-pushdown"></a>Aktivieren der Weitergabe

Die Schritte zum Aktivieren der Weitergabe werden im folgenden Artikel erläutert:

[Aktivieren der Weitergabeberechnung in Hadoop](polybase-configure-hadoop.md#pushdown)

## <a name="select-a-subset-of-rows"></a>Auswählen einer Teilmenge von Zeilen

Verwenden Sie die Prädikatweitergabe zum Verbessern der Leistung für eine Abfrage, die eine Teilmenge von Zeilen aus einer externen Tabelle auswählt.

In diesem Beispiel initiiert SQL Server 2016 einen map-reduce-Auftrag zum Abrufen der Zeilen, die dem Prädikat `customer.account_balance < 200000` auf Hadoop entsprechen. Da die Abfrage nicht erfolgreich abschließen kann, ohne alle Zeilen der Tabelle zu scannen, werden nur die Zeilen, die den Prädikatskriterien entsprechen, in SQL Server kopiert. Dies spart Zeit und erfordert weniger temporären Speicherplatz, wenn die Anzahl der Debitorensalden < 200000 im Vergleich mit der Anzahl der Kunden mit Kontensalden >= 200000 klein ist.

```sql
SELECT * FROM customer WHERE customer.account_balance < 200000
SELECT * FROM SensorData WHERE Speed > 65;  
```

### <a name="select-a-subset-of-columns"></a>Auswählen einer Teilmenge von Spalten

Verwenden Sie die Prädikatweitergabe zum Verbessern der Leistung für eine Abfrage, die eine Teilmenge von Spalten aus einer externen Tabelle auswählt.

In dieser Abfrage initiiert SQL Server einen map-reduce-Auftrag, um die auf Hadoop begrenzte Textdatei vorab zu verarbeiten, sodass nur die Daten der zwei Spalten customer.name und customer.zip_code in SQL Server PDW kopiert werden.

```sql
SELECT customer.name, customer.zip_code FROM customer WHERE customer.account_balance < 200000
```

### <a name="pushdown-for-basic-expressions-and-operators"></a>Weitergabe für grundlegende Ausdrücke und Operatoren

SQL Server erlaubt die folgenden grundlegenden Ausdrücke und Operatoren für Prädikatweitergabe.

+ Binäre Vergleichsoperatoren (\<, >, =, !=, <>, >=, <=) für die numerischen, Datums- und Zeitwerte.

+ Arithmetische Operatoren (+, -, *, /, %).

+ Logische Operatoren (AND, OR).

+ Unäroperatoren (NOT, IS NULL, IS NOT NULL).

Die Operatoren BETWEEN, NOT, IN und LIKE können möglicherweise weitergegeben werden. Das aktuelle Verhalten hängt davon ab, wie der Abfrageoptimierer die Operatorausdrücke als eine Reihe von Anweisungen neu schreibt, die grundlegende relationale Operatoren verwenden.

Die Abfrage in diesem Beispiel verfügt über mehrere Prädikate, die an Hadoop weitergegeben werden können. SQL Server kann map-reduce-Aufträge an Hadoop weitergeben, um das Prädikat `customer.account_balance <= 200000` auszuführen. Der Ausdruck `BETWEEN 92656 and 92677` besteht auch aus binären und logischen Operationen, die an Hadoop weitergegeben werden können. Das logische **AND** in `customer.account_balance and customer.zipcode` ist ein finaler Ausdruck.

Mit dieser Kombination von Prädikaten können also die map-reduce-Aufträge alle Bedingungen der WHERE-Klausel vollständig bearbeiten. Nur die Daten, die die Kriterien von SELECT erfüllen, werden in SQL Server PDW zurückkopiert.

```sql
SELECT * FROM customer WHERE customer.account_balance <= 200000 AND customer.zipcode BETWEEN 92656 AND 92677
```

## <a name="force-pushdown"></a>Weitergabe erzwingen

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (FORCE EXTERNALPUSHDOWN);
```

## <a name="disable-pushdown"></a>Weitergabe deaktivieren

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (DISABLE EXTERNALPUSHDOWN);
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie im [PolyBase-Leitfaden](polybase-guide.md).
