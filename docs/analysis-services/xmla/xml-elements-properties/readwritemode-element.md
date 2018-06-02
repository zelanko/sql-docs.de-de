---
title: ReadWriteMode-Element | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0d528567e22c3ba19b49eefff10d886703a0d29a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576492"
---
# <a name="readwritemode-element"></a>ReadWriteMode-Element
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Die **ReadWriteMode** -Datenbankeigenschaft gibt an, ob sich die Datenbank im **ReadWrite** -Modus oder im **ReadOnly** -Modus befindet. Hierbei handelt es sich um die beiden einzigen möglichen Werte der Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|ReadWrite|  
|Cardinality|0-1: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Datenbank](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Datenbanken können nur im **ReadWrite** -Modus erstellt werden. Datenbanken können nicht im **ReadOnly** -Modus erstellt werden.  
  
 Der Wert des **ReadWriteMode** -Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*readOnly*|Es können keine Änderungen oder Updates auf die Datenbank angewendet werden.|  
|*ReadWrite*|Es können Änderungen oder Updates auf die Datenbank angewendet werden.|  
  
## <a name="see-also"></a>Siehe auch
 [Attach-Element](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Anfügen und Trennen von Analysis Services-Datenbanken](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Verschieben einer Analysis Services-Datenbank](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Datenbank-ReadWriteModes](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Umschalten Sie in einer Analysis Services-Datenbank zwischen Schreib-und Lesemodus](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
