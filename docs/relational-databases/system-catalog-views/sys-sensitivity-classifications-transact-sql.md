---
title: sys. sensitivity_classifications (Transact-SQL) | Microsoft-Dokumentation
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
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
ms.openlocfilehash: a9d14cd93b08c0094ad984a6469b433e0b266479
ms.sourcegitcommit: 77293fb1f303ccfd236db9c9041d2fb2f64bce42
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929778"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sys. sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Gibt eine Zeile für jedes klassifizierte Element in der Datenbank zurück.

|Spaltenname|Datentyp|Beschreibung|
|-----------------|---------------|-----------------|  
|**class**|**int**|Identifiziert die Klasse des Elements, für das die Klassifizierung vorhanden ist.|  
|**class_desc**|**varchar (16)**|Eine Beschreibung der Klasse des Elements, für das die Klassifizierung vorhanden ist.|  
|**major_id**|**int**|ID des Elements, für das die Klassifizierung vorhanden ist. < \>BR < \>BR, wenn die Klasse 0 ist, ist major_id immer 0.<br>Wenn die Klasse den Wert 1, 2 oder 7 hat major_id ist object_id.|  
|**minor_id**|**int**|Sekundäre ID des Elements, für das die Klassifizierung vorhanden ist, interpretiert nach der Klasse.<br><br>Wenn class = 1, ist minor_id die column_id (if-Spalte), Else 0 (if-Objekt).<br>Wenn class = 2, ist minor_id der parameter_id.<br>Wenn class = 7, ist minor_id der index_id. |  
|**label**|**sysname**|Die Bezeichnung (Menschen lesbar), die für die Vertraulichkeits Klassifizierung zugewiesen ist.|  
|**label_id**|**sysname**|Eine ID, die der Bezeichnung zugeordnet ist und von einem Informationsschutz System wie z. b. Azure Information Protection (AIP) verwendet werden kann.|  
|**information_type**|**sysname**|Der Informationstyp (Menschen lesbar), der der Sensitivität-Klassifizierung zugewiesen ist.|  
|**information_type_id**|**sysname**|Eine ID, die dem Informationstyp zugeordnet ist und von einem Informationsschutz System wie z. b. Azure Information Protection (AIP) verwendet werden kann.|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Hinweise  

- Diese Ansicht bietet Einblick in den Klassifizierungs Status der Datenbank. Sie kann zum Verwalten der Daten Bank Klassifizierungen sowie zum Erstellen von Berichten verwendet werden.
- Derzeit wird nur die Klassifizierung von Daten Bank Spalten unterstützt. Damit
    - **Class** : hat immer den Wert 1 (die eine Spalte darstellt)
    - **class_desc** : hat immer den Wert *OBJECT_OR_COLUMN*
    - **major_id** -stellt die ID der Tabelle mit der klassifizierten Spalte dar, die sys. all _objects. object_id entspricht.
    - **minor_id** -stellt die ID der Spalte dar, für die die Klassifizierung vorhanden ist, entspricht sys. all _columns. column_id

## <a name="examples"></a>Beispiele

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Auflisten aller klassifizierten Spalten und der entsprechenden Klassifizierung

Im folgenden Beispiel wird eine Tabelle mit dem Tabellennamen, dem Spaltennamen, der Bezeichnung, der Bezeichnungs-ID, dem Informationstyp und der Informationstyp-ID für jede klassifizierte Spalte in der Datenbank zurückgegeben.

> [!NOTE]
> Bezeichnung ist ein Schlüsselwort für Azure SQL Data Warehouse.

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="see-also"></a>Siehe auch  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Azure SQL-Datenbank – Datenermittlung und -klassifizierung](https://aka.ms/sqlip)
