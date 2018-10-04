---
title: Mode-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e768d9ef176a05d4fe7622a520c9ac98f1d71d81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072410"
---
# <a name="mode-element-xmla"></a>Mode-Element (XMLA)
  Gibt den Modus vom übergeordneten Element verwendet werden [Sperre](../xml-elements-commands/lock-element-xmla.md) Element beim Erstellen einer Sperre für ein angegebenes Objekt.  
  
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
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Sperre](../xml-elements-commands/lock-element-xmla.md), [nicht entsperren](../xml-elements-commands/unlock-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das übergeordnete `Lock`-Element verwendet das `Mode`-Element, um den Typ der auf einem Objekt zu erstellenden Sperre zu bestimmen. Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*CommitShared*|Auf dem angegebenen Objekt wird eine gemeinsame Sperre erstellt. Andere gemeinsame Sperren können für das gleiche Objekt erstellt werden.<br /><br /> Eine gemeinsame Sperre verhindert, dass Transaktionen, die Schreibvorgänge enthalten wie ein [Execute](../xml-elements-methods-execute.md) Methodenaufruf Ausführen eine [Alter](../xml-elements-commands/alter-element-xmla.md) Befehl für ein angegebenes Objekt, ein Commit ausgeführt wird, bis die gemeinsame Sperre aufgehoben wird. Eine gemeinsame Sperre verhindert nicht, dass Transaktionen, die Lesevorgänge an, wie z. B. enthalten eine [Discover](../xml-elements-methods-discover.md) Methodenaufruf oder ein `Execute` Methodenaufruf ausgeführt wird ein [Anweisung](../xml-elements-commands/statement-element-xmla.md) Befehl, ein Commit ausgeführt wird.|  
|*CommitExclusive*|Auf dem angegebenen Objekt wird eine exklusive Sperre erstellt. Andere gemeinsame oder exklusive Sperren können nicht für das gleiche Objekt erstellt werden.<br /><br /> Eine exklusive Sperre verhindert die Commitausführung von Transaktionen, die entweder Lese- oder Schreibvorgänge auf einem angegebenen Objekt enthalten, bis die exklusive Sperre aufgehoben ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [ID-Element &#40;XMLA&#41;](id-element-xmla.md)   
 [Objekt-Element &#40;XMLA&#41;](object-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
