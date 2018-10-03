---
title: DISCOVER_XML_METADATA-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DISCOVER_XML_METADATA
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f902be22a044112b3801f3e0090e7faea5603ebf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228000"
---
# <a name="discoverxmlmetadata-rowset"></a>DISCOVER_XML_METADATA-Rowset
  Gibt ein XML-Dokument zurück, in dem ein angefordertes Objekt beschrieben wird. Das zurückgegebene Rowset besteht immer aus einer Zeile und einer Spalte.  
  
 Aufrufen der [ermitteln](../../xmla/xml-elements-methods-discover.md) -Methode mit der `DISCOVER_XML_METATDATA` Enumerationswert in der [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) -Element, die `Discover` Methode gibt die `DISCOVER_XML_METATDATA` Rowset.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_XML_METADATA` Rowset enthält die folgende Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`METADATA`|`DBTYPE_WSTR`||Ein XML-Dokument, das das von der Einschränkung angeforderte Objekt beschreibt.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
> [!IMPORTANT]  
>  Das `DISCOVER_XML_METADATA`-Rowset kann nicht mithilfe der SELECT-Befehlssyntax abgefragt werden. Das `DISCOVER_XML_METADATA`-Rowset kann jedoch mithilfe von <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> abgefragt werden.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_XML_METADATA` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`DatabaseID`|`DBTYPE_WSTR`|Optional.|  
|`DimensionID`|`DBTYPE_WSTR`|Optional.|  
|`CubeID`|`DBTYPE_WSTR`|Optional.|  
|`MeasureGroupID`|`DBTYPE_WSTR`|Optional.|  
|`PartitionID`|`DBTYPE_WSTR`|Optional.|  
|`PerspectiveID`|`DBTYPE_WSTR`|Optional.|  
|`DimensionPermissionID`|`DBTYPE_WSTR`|Optional.|  
|`RoleID`|`DBTYPE_WSTR`|Optional.|  
|`DatabasePermissionID`|`DBTYPE_WSTR`|Optional.|  
|`MiningModelID`|`DBTYPE_WSTR`|Optional.|  
|`MiningModelPermissionID`|`DBTYPE_WSTR`|Optional.|  
|`DataSourceID`|`DBTYPE_WSTR`|Optional.|  
|`MiningStructureID`|`DBTYPE_WSTR`|Optional.|  
|`AggregationDesignID`|`DBTYPE_WSTR`|Optional.|  
|`TraceID`|`DBTYPE_WSTR`|Optional.|  
|`MiningStructurePermissionID`|`DBTYPE_WSTR`|Optional.|  
|`CubePermissionID`|`DBTYPE_WSTR`|Optional.|  
|`AssemblyID`|`DBTYPE_WSTR`|Optional.|  
|`MdxScriptID`|`DBTYPE_WSTR`|Optional.|  
|`DataSourceViewID`|`DBTYPE_WSTR`|Optional.|  
|`DataSourcePermissionID`|`DBTYPE_WSTR`|Optional.|  
|`ObjectExpansion`|`DBTYPE_WSTR`|Optional.|  
  
 Die Einschränkung `ObjectExpansion`, steht für jedes Hauptobjekt von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Der Client verwendet normalerweise Einschränkungen, um die OLAP-Objekte zu beschreiben, für die der DDL-Code zurückgegeben wird, und er verwendet die `ObjectExpansion`-Einschränkung, um den Grad der Erweiterung im zurückgegebenen DDL-Code zu definieren. In der folgende Tabelle angibt, ob der Enumerationswert für [Alter-Element &#40;XMLA&#41; ](../../xmla/xml-elements-commands/alter-element-xmla.md) Befehle.  
  
|Enumerationswert|Description|  
|-----------------------|-----------------|  
|`ReferenceOnly`|Gibt nur den angeforderten Namen, den Timestamp, die ID und den Status für das angeforderte Objekt und alle nachfolgenden Hauptobjekte rekursiv zurück.|  
|`ObjectProperties`|Erweitert das angeforderte Objekt ohne Verweise auf enthaltene Objekte (schließt enthaltene erweiterte Nebenobjekte ein).|  
|`ExpandObject`|Wie *ObjectProperties*, gibt jedoch auch den Namen, die ID und den Timestamp für enthaltene Hauptobjekte zurück.|  
|`ExpandFull`|Erweitert das angeforderte Objekt vollständig rekursiv bis zum Ende eines jeden enthaltenen Objekts.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
