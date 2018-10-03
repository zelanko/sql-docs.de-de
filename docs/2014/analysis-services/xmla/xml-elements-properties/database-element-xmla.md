---
title: Database-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Database Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.database
- http://schemas.microsoft.com/analysisservices/2003/engine#Database
- urn:schemas-microsoft-com:xml-analysis#Database
helpviewer_keywords:
- Database element
ms.assetid: 2ded06c4-4eaf-4ccb-a416-41ee51ced8bc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5861be2ad0f5975ef5b95c3f4b077a065b560e02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171960"
---
# <a name="database-element-xmla"></a>Database-Element (XMLA)
  Identifiziert die Datenbank aus die Dimension dargestellt, die vom übergeordneten Element enthaltenen [Objekt](object-element-dimension-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Object>  
   ...  
   <Database>...</Database>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Objekt](object-element-dimension-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `Database` Element ist ein Objektbezeichner, der den Namen der Analysis Services-Datenbank, die Dimension enthält, dargestellt durch die `Object` Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element &#40;XMLA&#41;](cube-element-xmla.md)   
 [Dimension-Element &#40;XMLA&#41;](dimension-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
