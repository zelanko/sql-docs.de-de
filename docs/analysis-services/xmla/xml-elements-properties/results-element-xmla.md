---
title: Element (XMLA) führt | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7fc64d6b31f1b05d8bf5b4d1c80d75dff0583e86
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576162"
---
# <a name="results-element-xmla"></a>results-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Auflistung von [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) -Elementen, die von der [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) -Methode mit dem Befehl [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) zurückgegeben werden.  
  
 **Namespace** `http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Rückgabewert](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Untergeordnete Elemente|[Stamm](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein **Batch** -Befehl von der **Execute** -Methode ausgeführt wird, enthält das **return** -Element statt eines einzelnen **results** -Elements ein einzelnes **root** -Element. Der Inhalt des **results** -Elements hängt von den Einstellungen ab, die verwendet werden, um den Befehl **Batch** auszuführen.  
  
 Für nicht transaktionale **Batch** -Befehle enthält das **results** -Element ein **root** -Element für jeden Befehl, der vom **Batch** -Befehl ausgeführt wird, und zwar unabhängig davon, ob der Befehl erfolgreich abgeschlossen werden kann oder nicht. Für transaktionale **Batch** -Befehle enthält das **results** -Element nur ein **root** -Element, das die Fehlerinformationen für den Befehl enthält, der innerhalb des **Batch** -Befehls fehlgeschlagen ist.  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
