---
title: Sys.sensitivity_classifications (Transact-SQL) | Microsoft-Dokumentation
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: t-sql
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d0adbbeb82c06d6a44f3a7439bcbf479d7358401
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993792"
---
# <a name="syssensitivityclassifications-transact-sql"></a>Sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Gibt eine Zeile für jede klassifizierte Element in der Datenbank zurück.

|Spaltenname|Datentyp|Description|
|-----------------|---------------|-----------------|  
|**class**|**int**|Gibt die Klasse des Elements, auf dem die Klassifizierung vorhanden ist.|  
|**class_desc**|**varchar(16)**|Eine Beschreibung der Klasse des Elements, auf dem die Klassifizierung vorhanden ist.|  
|**major_id**|**int**|ID des Elements, auf denen die Klassifizierung vorhanden ist. < Br \>< Br \>Klasse 0 Major_id ist, immer 0.<br>Klasse ist 1, 2 oder 7 Major_id Object_id.|  
|**minor_id**|**int**|Sekundäre ID des Elements, auf dem die Klassifizierung vorhanden ist, interpretiert gemäß der entsprechenden Klasse.<br><br>Wenn Klasse = 1, Minor_id ist die Column_id (wenn Spalte), andernfalls 0 (wenn Objekt).<br>Wenn Klasse = 2, Minor_id ist die Parameter_id.<br>Wenn Klasse = 7, Minor_id ist die Index_id. |  
|**label**|**sysname**|Die Bezeichnung (lesbare) für die vertraulichkeitsklassifizierung zugewiesen|  
|**label_id**|**sysname**|Eine ID verknüpft ist, mit der Bezeichnung, die von einem Informationssystem Schutz wie Azure Information Protection (AIP) verwendet werden kann|  
|**information_type**|**sysname**|Der Informationstyp (lesbare) für die vertraulichkeitsklassifizierung zugewiesen|  
|**information_type_id**|**sysname**|Eine ID zugeordnet den Informationstyp an, die von einem Informationssystem Schutz wie Azure Information Protection (AIP) verwendet werden können|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Hinweise  

- Diese Ansicht bietet einen Einblick in die der klassifizierungsstatus der Datenbank. Es kann für die Verwaltung der Datenbank-Klassifizierungen sowie zur Erstellung von Berichten verwendet werden.
- Derzeit wird nur die Klassifizierung von Datenbankspalten wird unterstützt. Daher:
    - **Klasse** -weisen immer den Wert 1 (für eine Spalte)
    - **Class_desc** -besitzen immer den Wert *OBJECT_OR_COLUMN*
    - **Major_id** – stellt die ID der Tabelle, die die klassifizierte Spalte enthält, die entsprechende sys.all_objects.object_id dar
    - **Minor_id** – stellt die ID der Spalte auf dem die Klassifizierung vorhanden, entspricht sys.all_columns.column_id ist dar

## <a name="examples"></a>Beispiele

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Auflisten aller klassifizierten Spalten und der entsprechenden Klassifizierung

Das folgende Beispiel gibt eine Tabelle mit den Tabellennamen, Spaltennamen, Bezeichnung bezeichnungs-ID, Informationstyp Informations-Typ-ID für jede klassifizierte Spalte in der Datenbank.

```sql
SELECT
    sys.all_objects.name AS TableName, sys.all_columns.name As ColumnName,
    Label, Label_ID, Information_Type, Information_Type_ID
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="see-also"></a>Siehe auch  

[Fügen Sie die EMPFINDLICHKEIT CLASSIFICTION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[Löschen Sie die EMPFINDLICHKEIT CLASSIFICTION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Erste Schritte mit SQL Information Protection](http://aka.ms/sqlip)
