---
title: DISCOVER_STORAGE_TABLES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f5e645098da53c720d37814b4dc4dbfe6f1c76
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169551"
---
# <a name="discoverstoragetables-rowset"></a>DISCOVER_STORAGE_TABLES-Rowset
  Ermöglicht dem Client, die Tabellen zu bestimmen, die in einer im tabellarischen Modus oder SharePoint-Modus ausgeführten Analysis Services-Datenbank enthalten sind.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_STORAGE_TABLES` Rowset enthält die folgenden Spalten.  
  
|**Spaltenname**|**Typindikator**|**Länge**|**Beschreibung**|  
|---------------------|------------------------|----------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`||Gibt den Namen der Datenbank an, die die Tabellen enthält.<br /><br /> Die `DISCOVER_STORAGE_TABLES` Rowset kann mithilfe dieser Spalte eingeschränkt werden. Wenn diese Spalte nicht verwendet wird, um das Rowset einzuschränken, wird die aktuelle Datenbank verwendet.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Gibt den Cube oder das Modell an, das die Tabellen enthält.<br /><br /> Die `DISCOVER_STORAGE_TABLES` Rowset kann mithilfe dieser Spalte eingeschränkt werden.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`||Der Name der Measuregruppe.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`||Der Name der Partition.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Der Name der Dimension.|  
|`TABLE_ID`|`DBTYPE_WSTR`||Die ID der Tabelle, die verwendet wird, um die Tabellenattribute zu speichern.|  
|`TABLE_PARTITIONS_COUNT`|`DBTYPE_ WSTR`||Die Anzahl der Tabellenpartitionen.|  
|`HINT_TABLE_TYPE`|`DBTYPE_ WSTR`||Der Hinweis auf den Tabellentyp.|  
|`ROWS_COUNT`|`DBTYPE_UI4`||Anzahl der Zeilen in der Partition.|  
|`RIVIOLATION_COUNT`|`DBTYPE_UI4`||Die Anzahl der Zeilen mit Verstößen gegen die referenzielle Integrität.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_STORAGE_TABLES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|**Spaltenname**|**Typindikator**|**Einschränkungsstatus**|  
|---------------------|------------------------|---------------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Optional|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Optional|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird von der Standarddatenbank der aktuellen Verbindung eine Liste der Speichertabellen und die Anzahl der darin jeweils enthaltenen Zeilen zurückgegeben.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Schemarowsets](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
