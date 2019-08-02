---
title: Konvertierungen von Python- in SQL-Datentypen
description: Überprüfen Sie die impliziten und expliziten Datentyp Konvertierungen zwischen Python und SQL Server in Data Science und in Machine Learning-Lösungen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 690126098bbbd3ab26add51a0484f735120351de
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715784"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Datentyp Zuordnungen zwischen Python und SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Für python-Lösungen, die auf der python-Integrationsfunktion in SQL Server Machine Learning Services ausgeführt werden, überprüfen Sie die Liste der nicht unterstützten Datentypen und Datentyp Konvertierungen, die möglicherweise implizit ausgeführt werden, wenn Daten zwischen Python und SQL Server übermittelt werden.

## <a name="python-version"></a>Python-Version

Eine Teilmenge der revoscaler-Funktionalität (rxlinmod, rxlogit, rxvorhersage, rxdtrees, rxbtrees, eventuell einige andere) wird mithilfe von Python-APIs bereitgestellt. dabei wird ein neues Python-Paket **revoscalepy**verwendet. Sie können dieses Paket verwenden, um mit Daten zu arbeiten, die Pandas-Datenrahmen, Xdf-Dateien oder SQL-Daten Abfragen verwenden.

Weitere Informationen finden Sie unter [revoscalepy-Modul in SQL Server](ref-py-revoscalepy.md) -und [revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

Python unterstützt eine begrenzte Anzahl von Datentypen im Vergleich zu SQL Server. Wenn Sie Daten aus SQL Server in python-Skripts verwenden, werden die Daten daher möglicherweise implizit in einen kompatiblen Datentyp konvertiert. Häufig kann jedoch eine exakte Konvertierung nicht automatisch durchgeführt werden, und es wird ein Fehler zurückgegeben.

## <a name="python-and-sql-data-types"></a>Python-und SQL-Datentypen

In dieser Tabelle sind die impliziten Konvertierungen aufgeführt, die bereitgestellt werden. Andere Datentypen werden nicht unterstützt.

|SQLtype|Python-Typ|
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
