---
title: EventColumn-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EventColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EventColumn
helpviewer_keywords:
- EventColumn data type
ms.assetid: c0009f1d-d136-4155-9a1b-7baacda4b552
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 175504777bdba88ef434d275f136becc8241ada0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118040"
---
# <a name="eventcolumn-data-type-assl"></a>EventColumn-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der eine Spalte mit Informationen für die aufzuzeichnende darstellt ein [Ereignis](../objects/event-element-assl.md) -Element als Teil einer [Ablaufverfolgung](../objects/trace-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Spalten-ID](../properties/columnid-element-eventcolumn-assl.md)|  
|Abgeleitete Elemente|[Spalte](../objects/column-element-assl.md) ([Spalten](../collections/columns-element-assl.md) Auflistung von [Ablaufverfolgung](../objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>Siehe auch  
 [Events-Element &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
