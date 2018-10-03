---
title: Folder-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 70c5258edefa19d2858c40648aa742f75a9a1e49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055126"
---
# <a name="folder-element-xmla"></a>Folder-Element (XMLA)
  Enthält einen Dateisystem-Speicherort für aktualisiert werden eine [Speicherort](location-element-xmla.md) -Element während einer [wiederherstellen](../xml-elements-commands/restore-element-xmla.md) oder [synchronisieren](../xml-elements-commands/synchronize-element-xmla.md) Befehl.  
  
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
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ordner](folders-element-xmla.md)|  
|Untergeordnete Elemente|[Neue](new-element-xmla.md), [ursprünglichen](original-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Folder` -Element ändert, wenn angegeben, den Speicher Speicherorte der Objekte enthalten, entweder durch die Sicherungsdatei (für `Restore` Befehle) oder die Datenbank auf der Quellinstanz (für `Synchronize` Befehle), entsprechen den Wert des der `Original` zu den Wert der Elements der `New` Element.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [StorageLocation-Element &#40;ASSL&#41;](../../scripting/properties/storagelocation-element-assl.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
