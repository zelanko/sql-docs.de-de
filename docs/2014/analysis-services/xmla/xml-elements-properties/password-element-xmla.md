---
title: Password-Element (XMLA) | Microsoft Docs
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
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Password
- urn:schemas-microsoft-com:xml-analysis#Password
- microsoft.xml.analysis.password
helpviewer_keywords:
- Password element
ms.assetid: 8a0603bd-f6a1-4b86-84f1-c83d0b03951b
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cfc62de4ad73888fb95fe179efd0fdaeabbc9dc9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060800"
---
# <a name="password-element-xmla"></a>Password-Element (XMLA)
  Bestimmt das Kennwort, das vom übergeordneten Element verwendet werden [Backup](../xml-elements-commands/backup-element-xmla.md) oder [wiederherstellen](../xml-elements-commands/restore-element-xmla.md) -Befehl zum Verschlüsseln oder Entschlüsseln einer Sicherungsdatei.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Sicherung](../xml-elements-commands/backup-element-xmla.md), [wiederherstellen](../xml-elements-commands/restore-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein `Backup`-Befehl kein `Password`-Element oder eine leere Zeichenfolge enthält, wird die Sicherungsdatei nicht verschlüsselt.  
  
 Für `Restore` Befehle, wenn die `Password` Element nicht enthalten ist, oder eine leere Zeichenfolge enthält, bei dem Versuch, eine verschlüsselte Sicherungsdatei wiederherzustellen, ein Fehler auftritt.  
  
 Wenn `Location` -Elemente enthalten sind, entweder in eine `Backup` oder ein `Restore` dem Befehl `Password` Element wird für Sicherungsdateien für die sicherungs- und remotesicherungsdateien verwendet. Weitere Informationen zu remotesicherungsdateien finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Location-Element &#40;XMLA&#41;](location-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  