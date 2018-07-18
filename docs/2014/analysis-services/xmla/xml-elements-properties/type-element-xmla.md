---
title: Type-Element (XMLA) | Microsoft-Dokumentation
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
- Type Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 336266b8290f1a4eb10d200d8c1c31bf00f96879
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193780"
---
# <a name="type-element-xmla"></a>Type-Element (XMLA)
  Bestimmt den Typ des von auszuführenden Verarbeitung der [Prozess](../xml-elements-commands/process-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
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
|Übergeordnete Elemente|[Verarbeiten](../xml-elements-commands/process-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zum Verarbeiten von Optionen, die auf einer Instanz von Objekten zur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], finden Sie unter [mehrdimensionalen Modell Objekt verarbeitet](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Der Wert des der `Type` -Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*ProcessFull*|Löscht alle Daten im betroffenen Objekt und verarbeitet dann das betroffene Objekt.|  
|*ProcessAdd*|Fügt dem betroffenen Objekt neue Daten hinzu.|  
|*ProcessUpdate*|Aktualisiert die Daten im betroffenen Objekt.|  
|*ProcessIndexes*|Erstellt Indizes und Aggregationen im betroffenen Objekt oder erstellt diese neu.|  
|*ProcessScriptCache*|Wenn der Cube verarbeitet wird, erstellt der Server den MDX-Skriptcache neu. Wenn nicht, wird ein Fehler ausgelöst.<br /><br /> **Hinweis** Gilt nur für Cube.|  
|*ProcessData*|Verarbeitet Daten nur im betroffenen Objekt.|  
|*ProcessDefault*|Erkennt den Status des betroffenen Objekts und führt die geeignete Verarbeitungsoption am betroffenen Objekt durch, um eine vollständige Optimierung des Objekts zu erreichen und den Status der vollständigen Verarbeitung zurückzugeben.|  
|*ProcessClear*|Löscht die Daten im betroffenen Objekt und allen verknüpften Objekten.|  
|*ProcessStructure*|Verarbeitet nur die Struktur des betroffenen Objekts.|  
|*' ProcessClearStructureOnly '*|Löscht Daten nur aus dem betroffenen Objekt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
