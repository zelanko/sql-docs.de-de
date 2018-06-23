---
title: WritebackTableCreation-Element (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- WritebackTableCreation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#WritebackTableCreation
- microsoft.xml.analysis.writebacktablecreation
- http://schemas.microsoft.com/analysisservices/2003/engine#WritebackTableCreation
helpviewer_keywords:
- WritebackTableCreation element
ms.assetid: e9579d63-e28c-4d4e-9f4a-21c5da24c276
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 95b9639b34002aa69366f87cac48427624f7d0dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148172"
---
# <a name="writebacktablecreation-element-xmla"></a>WritebackTableCreation-Element (XMLA)
  Bestimmt, ob eine Rückschreibetabelle, während erstellt wird die [Prozess](../xml-elements-commands/process-element-xmla.md) Vorgang.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Verarbeiten](../xml-elements-commands/process-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Verarbeitungsoptionen verfügbar, um Objekte auf einer Analysis Services-Instanz, finden Sie unter [mehrdimensionalen Modell Objekt verarbeiten](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Der Wert, der die `WritebackTableCreation` -Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Erstellen*|Eine neue Rückschreibetabelle wird erstellt, sofern noch keine vorhanden ist. Wenn bereits eine Rückschreibetabelle vorhanden ist, tritt ein Fehler auf.|  
|*CreateAlways*|Eine neue Rückschreibetabelle wird erstellt, die jede vorhandene Rückschreibetabelle überschreibt.|  
|*"Useexisting"*|Die vorhandene Rückschreibetabelle wird verwendet, wenn bereits eine vorhanden ist. Wenn noch keine vorhanden ist, tritt ein Fehler auf.|  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  