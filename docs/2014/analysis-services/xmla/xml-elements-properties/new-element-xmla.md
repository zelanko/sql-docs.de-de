---
title: New-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- New Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#New
- microsoft.xml.analysis.new
- urn:schemas-microsoft-com:xml-analysis#New
helpviewer_keywords:
- New element
ms.assetid: 1321adcb-67f7-40f0-8f20-b17c1d3e3f17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 01f159352499625bf5065c96fcbd057590570610
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222380"
---
# <a name="new-element-xmla"></a>New-Element (XMLA)
  Enthält den neue Dateisystem-Speicherort ein, die eine [Ordner](folder-element-xmla.md) Element.  
  
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
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ordner](folder-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `New` Element enthält einen UNC-Pfad, der den Wert des ersetzt die `Original` vom übergeordneten Element enthaltene Element `Folder` -Element für alle Objekte wiederhergestellten oder synchronisierten, der während einer `Restore` oder `Synchronize` Befehl. Der Wert des der `Original` Element wird verglichen, auf den Wert des der `StorageLocation` -Element für jeden Cube, Measuregruppe oder Partition und, wenn eine Übereinstimmung gefunden wird, wird der Wert dieses Elements verwendet, Aktualisieren der `StorageLocation` des Objekts während der Wiederherstellung oder Synchronisierung.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [Backing Up and Restoring Objects (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Original-Element &#40;XMLA&#41;](original-element-xmla.md)   
 [Restore-Element &#40;XMLA&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [StorageLocation-Element &#40;ASSL&#41;](../../scripting/properties/storagelocation-element-assl.md)   
 [Synchronize-Element &#40;XMLA&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
