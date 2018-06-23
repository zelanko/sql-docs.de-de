---
title: DISCOVER_LOCATIONS-Rowset | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6d3a1171-8e4d-4022-ade0-b785cf795d70
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cfcc451a3369a3f15e29381df3d21e7275a90f7f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150453"
---
# <a name="discoverlocations-rowset"></a>DISCOVER_LOCATIONS-Rowset
  Gibt Informationen zum Inhalt einer Sicherungsdatei zurück. Sie müssen über die Berechtigung zum Zugreifen auf den Speicherort der Sicherungsdatei verfügen.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_LOCATIONS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`LOCATION_BACKUP_FILE_PATHNAME`|`DBTYPE_WSTR`|Erforderlich, siehe unten.|Der Speicherort der Sicherungsdatei.|  
|`LOCATION_PARTITION_OBJECTPATH`|`DBTYPE_WSTR`||Der Partitionspfad relativ zum Datenordner.|  
|`LOCATION_PARTITION_DATASOURCEID`|`DBTYPE_WSTR`||Die für die Verarbeitung der Partition verwendete Datenquellen-ID.|  
|`LOCATION_PARTITION_DATASOURCENAME`|`DBTYPE_WSTR`||Der Name der für die Verarbeitung verwendeten Datenquelle.|  
|`LOCATION_PARTITION_NAME`|`DBTYPE_WSTR`||Der Name der Partition.|  
|`LOCATION_PARTITION_SIZE`|`DBTYPE_WSTR`||Die ungefähre Größe der Partition.|  
|`LOCATION_CONNECTION_STRING`|`DBTYPE_WSTR`||Die Verbindungszeichenfolge der für die Verarbeitung verwendeten Datenquelle.|  
|`LOCATION_PARTITION_FOLDER`|`DBTYPE_WSTR`||Der ursprüngliche Speicherort dieser Partition, als die Sicherungsdatei erstellt wurde.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_LOCATIONS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`LOCATION_BACKUP_FILE_PATHNAME`|`DBTYPE_WSTR`|Required|  
|`LOCATION_PASSWORD PF_DBTYPE`|`DBTYPE_WSTR`|Erforderlich, falls während der Sicherung angegeben. Diese Einschränkung wird nicht verwendet, um die zurückgegebenen Zeilen einzuschränken. Wird verwendet, um das Kennwort bereitzustellen, damit auf den Speicherort zugegriffen werden kann.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Speicherorte|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  