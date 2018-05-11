---
title: Geben Sie-Element (Action) (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a82395be70c699da6fc96d3661aa71254e185883
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="type-element-action-assl"></a>Type-Element (Action) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält den Typ des der [Aktion](../../../analysis-services/scripting/objects/action-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Aktion](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*URL*|Zeigt eine veränderliche Seite in einem Internetbrowser an.|  
|*HTML*|Führt ein HTML-Skript in einem Internetbrowser aus.|  
|*Statement*|Führt einen OLE DB-Befehl aus.|  
|*DrillThrough*|Ruft ein Rowset für Drillthrough ab.<br /><br /> Dieser Wert ist mit *Rowset* identisch und identifiziert Drillthroughaktionen. Er kann nur bei Aktionen verwendet, deren [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) Wert wird festgelegt, um *Zellen*.|  
|*dataSet*|Ruft ein Dataset ab.|  
|*Rowset*|Ruft ein Rowset ab.|  
|*Befehlszeile*|Führt einen Befehl an einer Eingabeaufforderung aus.|  
|*Proprietäre*|Führt eine Operation aus, wobei eine andere Schnittstelle als die in der Tabelle zuvor aufgeführten verwendet wird.|  
|*Bericht*|Zeigt eine veränderliche Seite in einem Internetbrowser an.<br /><br /> Dieser Wert ist mit *Url* identisch und identifiziert Berichtsaktionen.|  
  
 Das Element, das das übergeordnete Element des entspricht **Typ** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [DrillThroughAction-Datentyp &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)   
 [ReportAction-Datentyp &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
