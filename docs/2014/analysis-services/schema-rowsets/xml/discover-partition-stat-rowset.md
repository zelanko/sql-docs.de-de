---
title: DISCOVER_PARTITION_STAT-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 749756c55a305997d49ae165b86e71a1fc756be7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129750"
---
# <a name="discoverpartitionstat-rowset"></a>DISCOVER_PARTITION_STAT-Rowset
  Gibt Statistiken zu Aggregationen in einer bestimmten Partition zurück.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_PARTITION_STAT` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Required|Der Name der Datenbank, welche die Dimension enthält.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Required|Der Namen des Cubes oder des Tabellenmodells mit der Partition.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Required|Der Name der Measuregruppe in der Dimension.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Required|Der Name einer Partition.<br /><br /> Diese Spalte ist in der Einschränkungsliste erforderlich.|  
|`AGGREGATION_NAME`|`DBTYPE_WSTR`||Der Name der Aggregation.|  
|`AGGREGATION_SIZE`|`DBTYPE_I8`||Die Größe der Aggregation.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
