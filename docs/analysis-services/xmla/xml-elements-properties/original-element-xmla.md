---
title: Original-Element (XMLA) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0ddf701f236e66680f562fa0721bcc8a2eb179f8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050388"
---
# <a name="original-element-xmla"></a>Original-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält den ursprünglichen Speicherort des Dateisystems ein, die eine [Ordner](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
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
 Die **ursprünglichen** Element enthält einen UNC-Pfad mit dem Wert ersetzt werden die [neu](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md) vom übergeordneten Element enthaltenen Elements **Ordner** -Element für alle Objekte wiederhergestellt oder synchronisiert werden, während eine [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) oder [synchronisieren](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) Befehl. Der Wert dieses Elements wird verglichen, auf den Wert des der [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md) -Element für jeden Cube, Measuregruppe oder Partition und, wenn eine Übereinstimmung gefunden wird, wird den Wert des der **neu** Element wird verwendet, um die Aktualisieren **StorageLocation** des Objekts während der Wiederherstellung oder Synchronisierung.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
