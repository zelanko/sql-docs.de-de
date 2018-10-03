---
title: DesignAggregations-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DesignAggregations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DesignAggregations
- microsoft.xml.analysis.designaggregations
- http://schemas.microsoft.com/analysisservices/2003/engine#DesignAggregations
helpviewer_keywords:
- DesignAggregations command
ms.assetid: 4c419dbc-7405-40aa-8ddd-6b46685a297d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c9ddcd70a0512273f816b633933b26fbf12d5b5a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058990"
---
# <a name="designaggregations-element-xmla"></a>DesignAggregations-Element (XMLA)
  Erstellt Aggregationen für einen Aggregationsentwurf auf einer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <DesignAggregations>  
      <Object>...</Object>  
      <Time>...</Time>  
      <Steps>...</Steps>  
      <Optimization>...</Optimization>  
      <Storage>...</Storage>  
      <Materialize>...</Materialize>  
      <Queries>...</Queries>  
   </DesignAggregations>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Materialisieren](../xml-elements-properties/materialize-element-xmla.md), [Objekt](../xml-elements-properties/object-element-xmla.md), [Optimierung](../xml-elements-properties/optimization-element-xmla.md), [Abfragen](../xml-elements-properties/queries-element-xmla.md), [Schritte](../xml-elements-properties/steps-element-xmla.md), [Storage](../xml-elements-properties/storage-element-xmla.md) , [Zeit](../xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `DesignAggregations` Befehl dient zum Generieren von Aggregationsdefinitionen, die von einem Aggregationsentwurf gespeichert werden. Ein Aggregationsentwurf kann dann verwendet werden, um Aggregationen für eine Partition zu materialisieren, und kann zwischen Partitionen neu verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
