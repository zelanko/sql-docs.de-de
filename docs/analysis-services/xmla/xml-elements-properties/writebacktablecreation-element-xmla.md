---
title: WritebackTableCreation-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fbbea11fcb4d7946e08e6c6045b2ecf17a1d40ff
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="writebacktablecreation-element-xmla"></a>WritebackTableCreation-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Bestimmt, ob eine Rückschreibetabelle, während erstellt wird die [Prozess](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) Vorgang.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Verarbeiten](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Verarbeitungsoptionen verfügbar, um Objekte auf einer Analysis Services-Instanz, finden Sie unter [Verarbeiten eines mehrdimensionalen Modells &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Der Wert des **WritebackTableCreation** -Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Create*|Eine neue Rückschreibetabelle wird erstellt, sofern noch keine vorhanden ist. Wenn bereits eine Rückschreibetabelle vorhanden ist, tritt ein Fehler auf.|  
|*CreateAlways*|Eine neue Rückschreibetabelle wird erstellt, die jede vorhandene Rückschreibetabelle überschreibt.|  
|*"Useexisting"*|Die vorhandene Rückschreibetabelle wird verwendet, wenn bereits eine vorhanden ist. Wenn noch keine vorhanden ist, tritt ein Fehler auf.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
