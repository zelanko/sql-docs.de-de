---
title: Objekt-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9ef2f645895e567d69d06e4e1383e0c477b6ed1
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575912"
---
# <a name="object-element-xmla"></a>Object-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält einen vom übergeordneten Element verwendeten Objektverweis.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Alter> <!-- or any of the parent elements in the Element relationships table -->  
...  
   <Object>  
      <!-- One or more object identifiers, depending on the parent element -->  
   </Object>  
...  
</Alter>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|Siehe Tabelle unten.|  
  
|Vorgänger oder übergeordnetes Element|Cardinality|  
|------------------------|-----------------|  
|[ALTER](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|0-1: Optionales Element, das nur einmal auftreten kann.|  
|Alle sonstigen|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), [Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md), [löschen](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md), [Sperre](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md), [Prozess](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), [abonnieren](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md), [synchronisieren](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Untergeordnete Elemente|Benötigt Analysis Services Scripting Language-XML-Elemente (ASSL). Durch das Auflisten der ID-Elemente des Objekts und seiner Vorgänger angegeben (mit Ausnahme der **Server** Objekt.) Beispielsweise die folgenden **Objekt** Element identifiziert eine Partition:<br /><br /> `<Object>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</Object>`|  
  
## <a name="remarks"></a>Hinweise  
 Die Reihenfolge, in der Bezeichner angezeigt werden, ist nicht wichtig.  
  
 Für **Alter** Elemente, die Instanz von Analysis Services wird als Standardobjekt verwendet, wenn die **Objekt** -Element nicht angegeben.  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
