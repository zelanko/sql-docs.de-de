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
ms.openlocfilehash: acb0043613c784b5677f3446beef22b6ecc12321
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="new-element-xmla"></a>New-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält den neuen von einem [Folder](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) -Element verwendeten Speicherort des Dateisystems.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Folder>  
   ...  
   <New>...</New>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ordner](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das **New** -Element enthält einen UNC-Pfad, der während eines **Original** - oder **Folder** -Befehls den Wert des **Restore** -Elements ersetzt, das im übergeordneten **Synchronize** -Element für alle wiederhergestellten oder synchronisierten Objekte enthalten ist. Der Wert des **Original** -Elements wird mit dem Wert des **StorageLocation** -Elements für die einzelnen Cubes, Measuregruppen oder Partitionen verglichen. Wenn eine Übereinstimmung festgestellt wird, wird der Wert dieses Elements für das Update der **StorageLocation** des Objekts während der Wiederherstellung oder Synchronisierung verwendet.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [Sichern und Wiederherstellen von Objekten (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Original-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)   
 [Restore-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [StorageLocation-Element & #40; ASSL & #41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Synchronisieren Sie-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
