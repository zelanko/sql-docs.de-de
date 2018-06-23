---
title: Mode-Element (XMLA) | Microsoft Docs
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
- Mode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords:
- Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5634e273e1708f9de213436e20008cc6874f50a7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163212"
---
# <a name="mode-element-xmla"></a>Mode-Element (XMLA)
  Gibt den Modus an, durch das übergeordnete Element verwendet werden [Sperre](../xml-elements-commands/lock-element-xmla.md) Element bei der Erstellung einer Sperre für ein angegebenes Objekt.  
  
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
|Übergeordnete Elemente|[Sperre](../xml-elements-commands/lock-element-xmla.md), [entsperren](../xml-elements-commands/unlock-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das übergeordnete `Lock`-Element verwendet das `Mode`-Element, um den Typ der auf einem Objekt zu erstellenden Sperre zu bestimmen. Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*CommitShared*|Auf dem angegebenen Objekt wird eine gemeinsame Sperre erstellt. Andere gemeinsame Sperren können für das gleiche Objekt erstellt werden.<br /><br /> Eine gemeinsame Sperre verhindert, dass Transaktionen, die mit der Schreibvorgänge, z. B. ein [Execute](../xml-elements-methods-execute.md) Methodenaufruf ausgeführt ein [Alter](../xml-elements-commands/alter-element-xmla.md) Befehl auf einem angegebenen Objekt, bis die gemeinsame Sperre aufgehoben wird. Eine gemeinsame Sperre verhindert nicht, dass Transaktionen, die Lesevorgänge an, wie z. B. enthalten eine [Discover](../xml-elements-methods-discover.md) Methodenaufruf oder ein `Execute` Methodenaufruf ausgeführt eine [Anweisung](../xml-elements-commands/statement-element-xmla.md) Befehl, ein Commit ausgeführt wird.|  
|*CommitExclusive*|Auf dem angegebenen Objekt wird eine exklusive Sperre erstellt. Andere gemeinsame oder exklusive Sperren können nicht für das gleiche Objekt erstellt werden.<br /><br /> Eine exklusive Sperre verhindert die Commitausführung von Transaktionen, die entweder Lese- oder Schreibvorgänge auf einem angegebenen Objekt enthalten, bis die exklusive Sperre aufgehoben ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [ID-Element &#40;XMLA&#41;](id-element-xmla.md)   
 [Objekt-Element &#40;XMLA&#41;](object-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  