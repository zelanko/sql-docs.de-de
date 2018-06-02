---
title: Subscribe-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f784cbe3c33eb6b2587b7b535668e793fac3b138
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574402"
---
# <a name="subscribe-element-xmla"></a>Subscribe-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Abonniert eine Ablaufverfolgung und gibt ein Rowset, das die Ablaufverfolgungsereignisse einer Analysis Services-Instanz zurück.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
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
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Objekt](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die **abonnieren** Befehl abonniert und Streams Sichern eines Rowsets aus einer angegebenen Ablaufverfolgung für eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Wenn ein anderes Objekt als die Ablaufverfolgung im **Object** -Element angegeben wird, tritt ein Fehler auf.  
  
 Wenn die **Objekt** Element nicht angegeben wird, eine sitzungsablaufverfolgung definiert und auf abonniert die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz. Die Sitzungsablaufverfolgung gibt einen festen Satz von Ablaufverfolgungsereignissen der aktuellen Sitzung zurück.  
  
 Der Rowset-Datenstrom zurückgegeben, die mit diesem Befehl wird beendet, wenn die Clientanwendung die Verbindung geschlossen wird die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz, oder, wenn die Sitzung auf dem die **abonnieren** Befehl wird ausgeführt, wird beendet.  
  
## <a name="see-also"></a>Siehe auch
 [Befehle &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
