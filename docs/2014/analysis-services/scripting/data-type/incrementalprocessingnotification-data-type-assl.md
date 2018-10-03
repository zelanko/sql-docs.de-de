---
title: IncrementalProcessingNotification-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IncrementalProcessingNotification Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotification data type
ms.assetid: 66e27f92-65c1-4a34-b9c2-bfbb5aeb7d7c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d02257847043aaa93db216d3d25cca91f9a76130
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068900"
---
# <a name="incrementalprocessingnotification-data-type-assl"></a>IncrementalProcessingNotification-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der Informationen des [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Elements über die Abfrage darstellt, die zum Bestimmen des Fortschritts der inkrementellen Verarbeitung ausgeführt werden muss.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<IncrementalProcessingNotification>  
   <!-- The following elements extend QueryNotification -->  
   <TableID>...</TableID>  
   <ProcessingQuery>...</ProcessingQuery>  
</IncrementalProcessingNotification>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[QueryNotification](../objects/querynotification-element-assl.md)|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[ProcessingQuery](../properties/query-element-assl.md), [TableID](../properties/id-element-assl.md)|  
|Abgeleitete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>Siehe auch  
 [ProactiveCachingQueryBinding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
