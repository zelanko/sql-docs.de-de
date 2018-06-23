---
title: EventColumn-Datentyp (ASSL) | Microsoft Docs
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
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f4e64defcd407e49b4f8e28d9034a2efeb440924
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149982"
---
# <a name="eventcolumn-data-type-assl"></a>EventColumn-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der eine Spalte mit Informationen für die aufzuzeichnenden darstellt ein [Ereignis](../objects/event-element-assl.md) -Element als Teil einer [Ablaufverfolgung](../objects/trace-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[ColumnID](../properties/columnid-element-eventcolumn-assl.md)|  
|Abgeleitete Elemente|[Spalte](../objects/column-element-assl.md) ([Spalten](../collections/columns-element-assl.md) Auflistung von [Ablaufverfolgung](../objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>Siehe auch  
 [Events-Element &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  