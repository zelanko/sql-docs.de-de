---
title: Type-Element (Action) (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af38eb6a60e8e54ecfc4ac5bb4fb05faeab69feb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168420"
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
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Aktion](../objects/action-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*URL*|Zeigt eine veränderliche Seite in einem Internetbrowser an.|  
|*HTML*|Führt ein HTML-Skript in einem Internetbrowser aus.|  
|*Anweisung*|Führt einen OLE DB-Befehl aus.|  
|*DrillThrough*|Ruft ein Rowset für Drillthrough ab.<br /><br /> Dieser Wert ist mit *Rowset* identisch und identifiziert Drillthroughaktionen. Es kann nur werden bei Aktionen verwendet, deren [TargetType](targettype-element-assl.md) Wert wird festgelegt, um *Zellen*.|  
|*DataSet*|Ruft ein Dataset ab.|  
|*Rowset*|Ruft ein Rowset ab.|  
|*Befehlszeile*|Führt einen Befehl an einer Eingabeaufforderung aus.|  
|*Proprietäre*|Führt eine Operation aus, wobei eine andere Schnittstelle als die in der Tabelle zuvor aufgeführten verwendet wird.|  
|*Bericht*|Zeigt eine veränderliche Seite in einem Internetbrowser an.<br /><br /> Dieser Wert ist mit *Url* identisch und identifiziert Berichtsaktionen.|  
  
 Das Element, das dem übergeordneten entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [DrillThroughAction-Datentyp &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [ReportAction-Datentyp &#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
