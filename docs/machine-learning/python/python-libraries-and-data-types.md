---
title: Konvertieren von Python- und SQL-Datentypen
description: Überprüfen Sie die implizite und explizite Konvertierung von Datentypen zwischen Python und SQL Server in Data Science- und Machine Learning-Lösungen.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 06/30/2020
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2efa4bc739dcf39cd10672d81ebf66eceb6ecbb8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85671115"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Zuordnungen von Datentypen zwischen Python und SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Überprüfen Sie für Python-Lösungen, die in der Python-Integrationsfunktion in SQL Server-Machine Learning Services ausgeführt werden, die Liste der nicht unterstützten Datentypen und Datentypkonvertierungen, die bei der Übergabe von Daten zwischen Python und SQL Server möglicherweise implizit ausgeführt werden.

## <a name="python-version"></a>Python-Version

Ein Teil der RevoScaleR-Funktionen (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees und eventuell weitere) wird mithilfe von Python-APIs bereitgestellt, die das neue Python-Paket **revoscalepy** verwenden. Sie können dieses Paket verwenden, um mithilfe von Pandas-Datenrahmen, XDF-Dateien oder SQL-Datenabfragen mit Daten zu arbeiten.

Weitere Informationen finden Sie unter [revoscalepy (Python-Modul in SQL Server)](ref-py-revoscalepy.md) und [revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

Verglichen mit SQL Server unterstützt Python nur eine begrenzte Anzahl von Datentypen. Daher ist es möglich, dass bei der Verwendung von Daten aus SQL Server in Python-Skripts diese implizit in einen kompatiblen Datentyp konvertiert werden. Da eine exakte automatische Konvertierung jedoch häufig nicht möglich ist, wird ein Fehler zurückgegeben.

## <a name="python-and-sql-data-types"></a>Python- und SQL-Datentypen

In der folgenden Tabelle werden die impliziten Konvertierungen aufgeführt, die bereitgestellt werden. Andere Datentypen werden nicht unterstützt.

|SQLType|Python-Typ|BESCHREIBUNG
|-------|-----------|---------------------------------------------------------------------------------------------|
|**bigint**|`float64`|
|**binary**|`bytes`|
|**bit**|`bool`|
|**char**|`str`|
|**date**|`datetime`|
|**datetime**|`datetime`|Dieser Typ wird in SQL Server 2017 CU6 und höher (mit **NumPy**-Arrays vom Typ `datetime.datetime` oder **Pandas** `pandas.Timestamp`) unterstützt. `sp_execute_external_script` unterstützt jetzt `datetime`-Typen mit Sekundenbruchteilen.|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float64`|
|**smalldatetime**|`datetime`|
|**smallint**|`int32`|
|**tinyint**|`int32`|
|**uniqueidentifier**|`str`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|
