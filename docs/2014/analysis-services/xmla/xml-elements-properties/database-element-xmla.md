---
title: Database-Element (XMLA) | Microsoft-Dokumentation
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
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22e385380b2757427b5fa3a33725f6c25e8dde36
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249430"
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
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Objekt](object-element-dimension-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `Database` Element ist ein Objektbezeichner, der den Namen der Analysis Services-Datenbank, die Dimension enthält, dargestellt durch die `Object` Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element &#40;XMLA&#41;](cube-element-xmla.md)   
 [Dimension-Element &#40;XMLA&#41;](dimension-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
