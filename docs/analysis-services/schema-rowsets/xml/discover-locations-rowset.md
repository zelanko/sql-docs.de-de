---
title: DISCOVER_LOCATIONS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d65e4ea55f956ce47632cd11a4e6dc5f8cfea377
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032751"
---
# <a name="discoverlocations-rowset"></a>DISCOVER_LOCATIONS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt Informationen zum Inhalt einer Sicherungsdatei zurück. Sie müssen über die Berechtigung zum Zugreifen auf den Speicherort der Sicherungsdatei verfügen.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_LOCATIONS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Erforderlich, siehe unten.|Der Speicherort der Sicherungsdatei.|  
|**LOCATION_PARTITION_OBJECTPATH**|**DBTYPE_WSTR**||Der Partitionspfad relativ zum Datenordner.|  
|**LOCATION_PARTITION_DATASOURCEID**|**DBTYPE_WSTR**||Die für die Verarbeitung der Partition verwendete Datenquellen-ID.|  
|**LOCATION_PARTITION_DATASOURCENAME**|**DBTYPE_WSTR**||Der Name der für die Verarbeitung verwendeten Datenquelle.|  
|**LOCATION_PARTITION_NAME**|**DBTYPE_WSTR**||Der Name der Partition.|  
|**LOCATION_PARTITION_SIZE**|**DBTYPE_WSTR**||Die ungefähre Größe der Partition.|  
|**LOCATION_CONNECTION_STRING**|**DBTYPE_WSTR**||Die Verbindungszeichenfolge der für die Verarbeitung verwendeten Datenquelle.|  
|**LOCATION_PARTITION_FOLDER**|**DBTYPE_WSTR**||Der ursprüngliche Speicherort dieser Partition, als die Sicherungsdatei erstellt wurde.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_LOCATIONS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Erforderlich|  
|**LOCATION_PASSWORD PF_DBTYPE**|**DBTYPE_WSTR**|Erforderlich, falls während der Sicherung angegeben. Diese Einschränkung wird nicht verwendet, um die zurückgegebenen Zeilen einzuschränken. Wird verwendet, um das Kennwort bereitzustellen, damit auf den Speicherort zugegriffen werden kann.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|Wert|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Speicherorte|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
