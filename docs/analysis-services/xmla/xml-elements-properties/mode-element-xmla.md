---
title: Mode-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 12e792c51b2f6feb3edb4e01c12dcf4809e2d4d4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575752"
---
# <a name="mode-element-xmla"></a>Mode-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Gibt den Modus an, durch das übergeordnete Element verwendet werden [Sperre](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) Element bei der Erstellung einer Sperre für ein angegebenes Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Lock>  
   ...  
   <Mode>...</Mode>  
   ...  
</Lock>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Sperre](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [entsperren](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das übergeordnete **Lock** -Element verwendet das **Mode** -Element, um den Typ der auf einem Objekt zu erstellenden Sperre zu bestimmen. Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*CommitShared*|Auf dem angegebenen Objekt wird eine gemeinsame Sperre erstellt. Andere gemeinsame Sperren können für das gleiche Objekt erstellt werden.<br /><br /> Eine gemeinsame Sperre verhindert, dass Transaktionen, die mit der Schreibvorgänge, z. B. ein [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methodenaufruf ausgeführt ein [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) Befehl auf einem angegebenen Objekt, bis die gemeinsame Sperre aufgehoben wird. Eine gemeinsame Sperre verhindert nicht, dass Transaktionen, die Lesevorgänge an, wie z. B. enthalten eine [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) Methodenaufruf oder ein **Execute** Methodenaufruf ausgeführt eine [Anweisung](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) -Befehl aus Ausführen eines Commits für.|  
|*CommitExclusive*|Auf dem angegebenen Objekt wird eine exklusive Sperre erstellt. Andere gemeinsame oder exklusive Sperren können nicht für das gleiche Objekt erstellt werden.<br /><br /> Eine exklusive Sperre verhindert die Commitausführung von Transaktionen, die entweder Lese- oder Schreibvorgänge auf einem angegebenen Objekt enthalten, bis die exklusive Sperre aufgehoben ist.|  
  
## <a name="see-also"></a>Siehe auch
 [ID-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)   
 [Objekt-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
