---
title: DISCOVER_STORAGE_TABLES-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b87759d736044febc89099d493fb357d7e5153b9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029291"
---
# <a name="discoverstoragetables-rowset"></a>DISCOVER_STORAGE_TABLES-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Ermöglicht dem Client, die Tabellen zu bestimmen, die in einer im tabellarischen Modus oder SharePoint-Modus ausgeführten Analysis Services-Datenbank enthalten sind.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_STORAGE_TABLES** -Rowset enthält die folgenden Spalten.  
  
|**Spaltenname**|**Typindikator**|**Länge**|**Beschreibung**|  
|---------------------|------------------------|----------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**||Gibt den Namen der Datenbank an, die die Tabellen enthält.<br /><br /> Das **DISCOVER_STORAGE_TABLES** -Rowset kann mithilfe dieser Spalte eingeschränkt werden. Wenn diese Spalte nicht verwendet wird, um das Rowset einzuschränken, wird die aktuelle Datenbank verwendet.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Gibt den Cube oder das Modell an, das die Tabellen enthält.<br /><br /> Das **DISCOVER_STORAGE_TABLES** -Rowset kann mithilfe dieser Spalte eingeschränkt werden.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**||Der Name der Measuregruppe.|  
|**PARTITION_NAME**|**DBTYPE_WSTR**||Der Name der Partition.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Der Name der Dimension.|  
|**TABLE_ID**|**DBTYPE_WSTR**||Die ID der Tabelle, die verwendet wird, um die Tabellenattribute zu speichern.|  
|**TABLE_PARTITIONS_COUNT**|**DBTYPE_ WSTR**||Die Anzahl der Tabellenpartitionen.|  
|**HINT_TABLE_TYPE**|**DBTYPE_ WSTR**||Der Hinweis auf den Tabellentyp.|  
|**ROWS_COUNT**|**DBTYPE_UI4**||Anzahl der Zeilen in der Partition.|  
|**RIVIOLATION_COUNT**|**DBTYPE_UI4**||Die Anzahl der Zeilen mit Verstößen gegen die referenzielle Integrität.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_STORAGE_TABLES** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|**Spaltenname**|**Typindikator**|**Einschränkungsstatus**|  
|---------------------|------------------------|---------------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Optional|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|Optional|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird von der Standarddatenbank der aktuellen Verbindung eine Liste der Speichertabellen und die Anzahl der darin jeweils enthaltenen Zeilen zurückgegeben.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Schemarowsets](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
