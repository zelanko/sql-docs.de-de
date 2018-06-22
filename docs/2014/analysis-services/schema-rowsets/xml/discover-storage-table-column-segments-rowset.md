---
title: DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS-Rowset | Microsoft Docs
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2155e4a905da3aeade0f0789f05cc04cdd42f8d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047908"
---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS-Rowset
  Stellt Informationen zu Speichertabellen auf Spalten- und Segmentebene bereit, die von einer im tabellarischen oder PowerPivot-Modus ausgeführten Analysis Services-Datenbank verwendet werden. Dieses Rowset wird hauptsächlich für Problembehandlung und Analyse verwendet.  
  
 **Gilt für:** tabellarische Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS` Rowset enthält die folgenden Spalten.  
  
|**Spaltenname**|**Typindikator**|**Einschränkung**|**Beschreibung**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|ja|Gibt die tabellarische Datenbank an.<br /><br /> Die `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS` Rowset kann mithilfe dieser Spalte eingeschränkt werden. Wenn die aktuelle Datenbank ausgelassen wird verwendet.|  
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
|`VERTIPAQ_STATE`|`DBTYPE_WSTR`||Der Status der VertiPaq-Komprimierung für dieses Spaltensegment. Der Wert ist eine der folgenden:<br /><br /> -SKIPPED – wurde der Überprüfungsschritt ausgelassen.<br />-ABGESCHLOSSEN – der Überprüfungsschritt erfolgreich abgeschlossen.<br />-TIMEBOXED – die VertiPaq-Komprimierung wurde eingegrenzte.|  
  
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
  
  