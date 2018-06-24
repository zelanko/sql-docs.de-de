---
title: Geben Sie-Element (Action) (ASSL) | Microsoft Docs
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
- Type Element (Action)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d71abdd26cea5fa03c8e70f882f893878a70969a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058991"
---
# <a name="type-element-action-assl"></a>Type-Element (Action) (ASSL)
  Enthält den Typ des der [Aktion](../objects/action-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
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
|Übergeordnetes Element|[Aktion](../objects/action-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*URL*|Zeigt eine veränderliche Seite in einem Internetbrowser an.|  
|*HTML*|Führt ein HTML-Skript in einem Internetbrowser aus.|  
|*Anweisung*|Führt einen OLE DB-Befehl aus.|  
|*DrillThrough*|Ruft ein Rowset für Drillthrough ab.<br /><br /> Dieser Wert ist mit *Rowset* identisch und identifiziert Drillthroughaktionen. Er kann nur bei Aktionen verwendet, deren [TargetType](targettype-element-assl.md) Wert wird festgelegt, um *Zellen*.|  
|*DataSet*|Ruft ein Dataset ab.|  
|*Rowset*|Ruft ein Rowset ab.|  
|*Befehlszeile*|Führt einen Befehl an einer Eingabeaufforderung aus.|  
|*Proprietäre*|Führt eine Operation aus, wobei eine andere Schnittstelle als die in der Tabelle zuvor aufgeführten verwendet wird.|  
|*Bericht*|Zeigt eine veränderliche Seite in einem Internetbrowser an.<br /><br /> Dieser Wert ist mit *Url* identisch und identifiziert Berichtsaktionen.|  
  
 Das Element, das das übergeordnete Element des entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [DrillThroughAction-Datentyp &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [ReportAction-Datentyp &#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  