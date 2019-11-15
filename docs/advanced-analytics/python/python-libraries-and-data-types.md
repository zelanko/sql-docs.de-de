---
title: Konvertieren von Python- und SQL-Datentypen
description: Überprüfen Sie die implizite und explizite Konvertierung von Datentypen zwischen Python und SQL Server in Data Science- und Machine Learning-Lösungen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f22f838bc78d4791e73a1d107cd253aae314d205
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727519"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Zuordnungen von Datentypen zwischen Python und SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Überprüfen Sie für Python-Lösungen, die in der Python-Integrationsfunktion in SQL Server-Machine Learning Services ausgeführt werden, die Liste der nicht unterstützten Datentypen und Datentypkonvertierungen, die bei der Übergabe von Daten zwischen Python und SQL Server möglicherweise implizit ausgeführt werden.

## <a name="python-version"></a>Python-Version

Ein Teil der RevoScaleR-Funktionen (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees und eventuell weitere) wird mithilfe von Python-APIs bereitgestellt, die das neue Python-Paket **revoscalepy** verwenden. Sie können dieses Paket verwenden, um mithilfe von Pandas-Datenrahmen, XDF-Dateien oder SQL-Datenabfragen mit Daten zu arbeiten.

Weitere Informationen finden Sie unter [revoscalepy (Python-Modul in SQL Server)](ref-py-revoscalepy.md) und [revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

Verglichen mit SQL Server unterstützt Python nur eine begrenzte Anzahl von Datentypen. Daher ist es möglich, dass bei der Verwendung von Daten aus SQL Server in Python-Skripts diese implizit in einen kompatiblen Datentyp konvertiert werden. Da eine exakte automatische Konvertierung jedoch häufig nicht möglich ist, wird ein Fehler zurückgegeben.

## <a name="python-and-sql-data-types"></a>Python- und SQL-Datentypen

In der folgenden Tabelle werden die impliziten Konvertierungen aufgeführt, die bereitgestellt werden. Andere Datentypen werden nicht unterstützt.

|SQLType|Python-Typ|
|-------|-----------|
|**bigint**|`numeric`|
|**binary**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|
