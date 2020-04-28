---
title: Sequenzen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SEQUENCES
- SEQUENCES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SEQUENCES view
- INFORMATION_SCHEMA.SEQUENCES view
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ff8490824c6a0ccb45b383535e830cabff83407
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "77479348"
---
# <a name="sequences-transact-sql"></a>Sequenzen (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Gibt für jede Sequenz, auf die der aktuelle Benutzer in der aktuellen Datenbank zugreifen kann, eine Zeile zurück.

Zum Abrufen von Informationen aus diesen Sichten geben Sie den voll qualifizierten Namen **INFORMATION_SCHEMA**_. view_name_an.

|Spaltenname|Datentyp|BESCHREIBUNG|
|-----------------|---------------|-----------------|
|**SEQUENCE_CATALOG**|**nvarchar(128)**|Sequenz Qualifizierer|
|**SEQUENCE_SCHEMA**|**nvarchar (** 128) * *|Name des Schemas, das die Sequenz enthält|
|**SEQUENCE_NAME**|**nvarchar(128)**|Sequenzname|
|**DATA_TYPE**|**nvarchar (** 128 **)**|Der Sequenz Datentyp.|
|**NUMERIC_PRECISION**|**tinyint**|Die Genauigkeit der Sequenz.|
|**NUMERIC_PRECISION_RADIX**|**smallint**|Basis der Genauigkeit für Spalten mit ungefähren numerischen Daten, exakten numerischen Daten, ganzzahligen Daten oder Währungsdaten. Andernfalls wird NULL zurückgegeben.|
|**NUMERIC_SCALE**|**int**|Anzahl der Dezimalstellen für Spalten mit ungefähren numerischen Daten, exakten numerischen Daten, ganzzahligen Daten oder Währungsdaten. Andernfalls wird NULL zurückgegeben.|
|**START_VALUE**|**int**|Der erste Wert, der vom Sequenzobjekt zurückgegeben wird.|
|**MINIMUM_VALUE**|**int**|Die Begrenzungen für das Sequenz Objekt. Der minimale Standardwert eines neuen Sequenzobjekts ist gleich dem minimalen Wert für den Datentyp des Sequenzobjekts. Dieser ist für den tinyint -Datentyp 0 und für alle anderen Datentypen eine negative Zahl.|
|**MAXIMUM_VALUE**|**int**|Die Begrenzungen für das Sequenz Objekt. Der maximale Standardwert eines neuen Sequenzobjekts ist gleich dem maximalen Wert für den Datentyp des Sequenzobjekts.|
|**Inkrement**|**int**|Wert, um den der Wert des Sequenzobjekts bei jedem Aufruf der NEXT VALUE FOR-Funktion inkrementiert (oder bei negativem Wert dekrementiert) wird. Wenn als Inkrement ein negativer Wert verwendet wird, ist der Wert des Sequenzobjekts absteigend, andernfalls ist er aufsteigend. Das Inkrement kann nicht 0 sein. Das Standardinkrement für ein neues Sequenzobjekt ist 1.
|**CYCLE_OPTION**|**int**|Eigenschaft, die angibt, ob das Sequenzobjekt vom minimalen Wert (oder bei absteigenden Sequenzobjekten vom maximalen Wert) neu gestartet oder ob eine Ausnahme ausgelöst werden soll, wenn der minimale oder maximale Wert überschritten wird. Die Standardzyklusoption für neue Sequenzobjekte ist NO CYCLE.
|**DECLARED_DATA_TYPE**|**int**|Der Datentyp für den benutzerdefinierten Datentyp.|
|**DECLARED_DATA_PRECISION**|**int**|Die Genauigkeit für den benutzerdefinierten Datentyp.|
|**DECLARED_NUJMERIC_SCALE**|**int**|Die numerische Skala für den benutzerdefinierten Datentyp.|

**Beispiel** Im folgenden Beispiel werden Informationen zu den Schemas in der Testdatenbank zurückgegeben:

```sql
SELECT * FROM test.INFORMATION_SCHEMA.SEQUENCES;
```

## <a name="see-also"></a>Weitere Informationen

- [Informations Schema Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)
- [sys.sequences &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md)
