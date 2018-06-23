---
title: Tuple-Element (XMLA) | Microsoft Docs
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
- Tuple Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.tuple
- urn:schemas-microsoft-com:xml-analysis#Tuple
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuple
helpviewer_keywords:
- Tuple element
ms.assetid: d65aba10-55e1-49c1-81bc-0756c39c0da2
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: fe470d60aa008723034e1bdbf95f3ecf593c8a3a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061462"
---
# <a name="tuple-element-xmla"></a>Tuple-Element (XMLA)
  Enthält eine Sammlung von [Member](member-element-xmla.md)-Elementen, die im übergeordneten [Tuples](tuples-element-xmla.md)-Element enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
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
|Übergeordnete Elemente|[Tupel](tuples-element-xmla.md)|  
|Untergeordnete Elemente|[Datenmember](member-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Clientanwendung legt die `AxisFormat` Eigenschaft *' TupleFormat '*, eine Achse wird als eine Menge von Tupeln dargestellt. Jede `Axis` Element enthält eine `Tuples` Element, das die Tupelmenge auf dieser Achse darstellt. Jedes Tupel wird mithilfe eines `Tuple`-Elements dargestellt, das `Member`-Elemente aus jeder Hierarchie auf der Achse enthält.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Struktur der `Tuple` -Element, wenn ein Client gibt *' TupleFormat '* oder *CustomFormat* für die `AxisFormat` XMLA-Eigenschaft, die bei Angabe der folgenden Mitglieder für die Achse:  
  
|||||  
|-|-|-|-|  
|`Time`-Hierarchie|1999|1999|2000|  
|`Category`-Hierarchie|Tatsächlich|Budget|Budget|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  