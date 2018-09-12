---
title: Python-Bibliotheken und-Datentypen in SQL Server-Machine Learning | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 384c8c94bdef65e41af999848c9bac63fc0c8d40
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888366"
---
# <a name="python-libraries-and-data-types"></a>Python-Bibliotheken und -Datentypen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Python-Bibliotheken, die mit SQL Server Machine Learning Services (Datenbankintern) und (Standalone) Installation enthalten sind.

In diesem Artikel werden auch nicht unterstützten Datentypen aufgeführt, und listet die datentypkonvertierungen, die möglicherweise implizit durchgeführt werden, wenn Daten zwischen Python und SQL Server übergeben werden.

## <a name="python-version"></a>Python-Version

4.2 für SQL Server 2017 Anaconda-Distribution und Python 3.6.

Ein Teil der RevoScaleR-Funktionen (RxLinMod, RxLogit, RxPredict, RxDTrees, RxBTrees, vielleicht einige andere) wird unter Verwendung von Python-APIs, mit der ein neues Python-Paket bereitgestellt **Revoscalepy**. Sie können dieses Paket verwenden, arbeiten mit Daten, die mithilfe von Pandas-Datenrahmen, XDF-Dateien oder SQL Data-Abfragen.

Weitere Informationen finden Sie unter [Neuerungen Revoscalepy?](what-is-revoscalepy.md).

Python unterstützt eine begrenzte Anzahl von Datentypen im Vergleich zu SQL Server. Wenn Sie Daten aus SQL Server in Python-Skripts verwenden, können daher Daten implizit in einen kompatiblen Datentyp konvertiert. Allerdings häufig eine exakte Konvertierung nicht automatisch durchgeführt werden, und ein Fehler zurückgegeben.

## <a name="python-and-sql-data-types"></a>Python und SQL-Datentypen

Diese Tabelle enthält die impliziten Konvertierungen, die bereitgestellt werden. Andere Datentypen werden nicht unterstützt.

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



