---
title: DMSCHEMA_MINING_MODEL_XML-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_MODEL_XML
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_XML rowset
ms.assetid: f58b00e9-3f72-4cff-b448-21a9fb529772
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3be57336379c66577c245a891e047ec95f763fd9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130820"
---
# <a name="dmschemaminingmodelxml-rowset"></a>DMSCHEMA_MINING_MODEL_XML-Rowset
  Gibt die XML-Struktur des Miningmodells wieder. Das Format der XML-Zeichenfolge entspricht dem Standard der Predictive Model Markup Language (PMML 2.1).  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_MODEL_XML` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Der Katalogname. Wird mit dem Namen der Datenbank aufgefüllt, von der das Modell ein Element ist.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Der nicht gekennzeichnete Schemaname. Die Spalte wird von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Der Name des Modells. Diese Spalte darf nicht enthalten `NULL`.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Der Modelltyp. Dies ist eine anbieterspezifische Zeichenfolge. Diese kann `NULL` sein.|  
|`MODEL_GUID`|`DBTYPE_GUID`||Der GUID, der das Modell identifiziert. Anbieter, die keine GUIDs verwenden, um Tabellen zu identifizieren, geben `NULL` zurück.|  
|`MODEL_PMML`|`DBTYPE_WSTR`||Eine XML-Wiedergabe des Modellinhalts im PMML-Format.|  
|`SIZE`|`DBTYPE_UI4`||Die Anzahl der Bytes in der XML-Zeichenfolge.|  
|`LOCATION`|`DBTYPE_WSTR`||Der Speicherort der XML-Datei. Der Wert ist `NULL`, wenn keine physische Datei zum Speichern verwendet wird.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das DMSCHEMA_MINING_MODEL_XML-Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_W`STR|Optional.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
