---
title: DISCOVER_PARTITION_DIMENSION_STAT-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: bf4626b3-4d6b-4795-bb01-df335fb9c09a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 60b22e48479c185b1757227cd6cd2a19cb295199
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062650"
---
# <a name="discoverpartitiondimensionstat-rowset"></a>DISCOVER_PARTITION_DIMENSION_STAT-Rowset
  Gibt Statistiken zur Dimension zurück, die einer Partition zugeordnet ist.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_PARTITION_DIMENSION_STAT` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Required|Der Name der Datenbank.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Required|Der Namen des Cubes oder des Tabellenmodells.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Required|Der Name der Measuregruppe.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Required|Der Name der Partition.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Der Name der Dimension.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Der Name eines Attributs in der Dimension.|  
|`ATTRIBUTE_INDEXED`|`DBTYPE_BOOL`||true, um anzugeben, dass das Attribut indiziert ist; andernfalls false.|  
|`ATTRIBUTE_COUNT_MIN`|`DBTYPE_I8`||Mindestanzahl für das Attribut.|  
|`ATTRIBUTE_COUNT_MAX`|`DBTYPE_I8`||Maximale Anzahl für das Attribut.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
