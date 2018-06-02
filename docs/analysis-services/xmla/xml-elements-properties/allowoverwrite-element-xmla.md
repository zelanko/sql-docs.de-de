---
title: AllowOverwrite-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 76ba7c6b3046e5298a346cb84472de3ba090e2bc
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577522"
---
# <a name="allowoverwrite-element-xmla"></a>AllowOverwrite-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Bestimmt, ob das übergeordnete Element [Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) oder [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) Befehl wird versucht, die Zieldatei oder die Datenbank zu überschreiben.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <AllowOverwrite>...</AllowOverwrite>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Bei **Backup** -Befehlen bestimmt das **AllowOverwrite** -Element, ob der Befehl die Sicherungsdatei, die im **File** -Element angegeben ist, überschreiben darf.  
  
 Für **wiederherstellen** Elemente, die **AllowOverwrite** -Element bestimmt, ob der Befehl im angegebenen Analysis Services-Datenbank überschrieben werden kann die **DatabaseName** Element.  
  
## <a name="see-also"></a>Siehe auch
 [DatabaseName-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/databasename-element-xmla.md)   
 [Datei Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
