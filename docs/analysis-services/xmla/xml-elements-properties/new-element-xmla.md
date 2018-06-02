---
title: New-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ed98ed9c42d8cecddb07941855403925b1de6b8
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575922"
---
# <a name="new-element-xmla"></a>New-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält den neuen Speicherort im Dateisystem, in einem [Ordner](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Folder>  
   ...  
   <New>...</New>  
   ...  
</Folder>  
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
|Übergeordnete Elemente|[Ordner](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das **New** -Element enthält einen UNC-Pfad, der während eines **Original** - oder **Folder** -Befehls den Wert des **Restore** -Elements ersetzt, das im übergeordneten **Synchronize** -Element für alle wiederhergestellten oder synchronisierten Objekte enthalten ist. Der Wert des **Original** -Elements wird mit dem Wert des **StorageLocation** -Elements für die einzelnen Cubes, Measuregruppen oder Partitionen verglichen. Wenn eine Übereinstimmung festgestellt wird, wird der Wert dieses Elements für das Update der **StorageLocation** des Objekts während der Wiederherstellung oder Synchronisierung verwendet.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [Backing Up and Restoring Objects (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch
 [Original-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)   
 [Restore-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [StorageLocation-Element &#40;ASSL&#41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Synchronize-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
