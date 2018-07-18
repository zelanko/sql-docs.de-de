---
title: DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS-Rowset | Microsoft-Dokumentation
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
ms.assetid: 3e514715-9fe6-4e6a-accb-4149ffd7e0bf
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ae9955e9f052e4be2317206d5618ccf9294232cb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325020"
---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS-Rowset
  Stellt Informationen zu Speichertabellen auf Spalten- und Segmentebene bereit, die von einer im tabellarischen oder PowerPivot-Modus ausgeführten Analysis Services-Datenbank verwendet werden. Dieses Rowset wird hauptsächlich für Problembehandlung und Analyse verwendet.  
  
 **Gilt für:** tabellarische Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS` Rowset enthält die folgenden Spalten.  
  
|**Spaltenname**|**Typindikator**|**Einschränkung**|**Beschreibung**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|ja|Gibt die tabellarische Datenbank an.<br /><br /> Die `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS` Rowset kann mithilfe dieser Spalte eingeschränkt werden. Wenn die aktuelle Datenbank nicht angegeben, wird verwendet.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|ja|Der Name des Modells.<br /><br /> Die `DISCOVER_STORAGE_TABLES` Rowset kann mithilfe dieser Spalte eingeschränkt werden.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|ja|Der Name der Measuregruppe.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|ja|Der Name der Partition.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Der Name der Dimension.|  
|`TABLE_ID`|`DBTYPE_WSTR`||Die interne ID des Tabellensegments.|  
|`COLUMN_ID`|`DBTYPE_WSTR`||Die interne ID der Spalte.|  
|`SEGMENT _NUMBER`|`DBTYPE_I8`||Die Ordnungszahl des Tabellensegments.|  
|`TABLE_PARTTION_NUMBER`|`DBTYPE_I8`||Die Ordnungszahl der Partition.|  
|`RECORDS_COUNT`|`DBTYPE_I8`||Die Anzahl der Datensätze in der Partition.|  
|`ALLOCATED_SIZE`|`DBTYPE_UI8`||Dem Spaltensegment zugeordnete Größe in Byte.|  
|`USED_SIZE`|`DBTYPE_UI8`||Vom Spaltensegment verwendete Größe in Byte.|  
|`COMPRESSION_TYPE`|`DBTYPE_WSTR`||Typ der für das Spaltensegment verwendeten Komprimierung. Dieser Wert ist ausschließlich für die interne Verwendung und Kundensupportzwecke bestimmt. Microsoft veröffentlicht keine gültigen Werte oder Beschreibungen für diese Spalte.|  
|`BITS_COUNT`|`DBTYPE_I8`||Die Anzahl der Bits.|  
|`BOOKMARK_BITS_COUNT`|`DBTYPE_I8`||Die Anzahl der Lesezeichenbits.|  
|`VERTIPAQ_STATE`|`DBTYPE_WSTR`||Der Status der VertiPaq-Komprimierung für dieses Spaltensegment. Der Wert ist eine der folgenden:<br /><br /> -Die VertiPaq-Komprimierung wurde übersprungen, SKIPPED – klicken.<br />-ABGESCHLOSSEN – die VertiPaq-Komprimierung wurde erfolgreich abgeschlossen.<br />-TIMEBOXED – der VertiPaq-Komprimierung wurde Timeboxed.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd45-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageSegments|  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage gibt die dem Modellattribut "LastName" zugeordneten Speichertabellensegmente in der aktuellen Datenbank zurück.  
  
```  
SELECT DISTINCT TABLE_ID, COLUMN_ID   
FROM $system.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS  
WHERE COLUMN_ID = 'LastName'  
ORDER BY TABLE_ID  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Schemarowsets](../analysis-services-schema-rowsets.md)  
  
  
