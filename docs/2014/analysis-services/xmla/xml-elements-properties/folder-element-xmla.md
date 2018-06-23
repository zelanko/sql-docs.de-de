---
title: Folder-Element (XMLA) | Microsoft Docs
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
- Folder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.folder
- http://schemas.microsoft.com/analysisservices/2003/engine#Folder
- urn:schemas-microsoft-com:xml-analysis#Folder
helpviewer_keywords:
- Folder element
ms.assetid: 87b305b0-57e3-4ec3-9d80-f1bcf3ce7540
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 64bc73db4cfb1fee4471e474bf498094751edcf5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058992"
---
# <a name="folder-element-xmla"></a>Folder-Element (XMLA)
  Enthält einen Speicherort im Dateisystem aktualisiert werden muss eine [Speicherort](location-element-xmla.md) -Element während einer [wiederherstellen](../xml-elements-commands/restore-element-xmla.md) oder [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Folders>  
   ...  
   <Folder>  
      <Original>...</Original>  
      <New>...</New>  
   </Folder>  
   ...  
</Folders>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ordner](folders-element-xmla.md)|  
|Untergeordnete Elemente|[Neue](new-element-xmla.md), [ursprünglichen](original-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Folder` Element, wenn angegeben wird, ändert sich den Speicher Positionen von Objekten enthalten, entweder durch die Sicherungsdatei (für `Restore` Befehle) oder die Datenbank auf der Quellinstanz (für `Synchronize` Befehle), die den Wert der entsprechen der `Original` -Elements auf den Wert, der die `New` Element.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [StorageLocation-Element &#40;ASSL&#41;](../../scripting/properties/storagelocation-element-assl.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  