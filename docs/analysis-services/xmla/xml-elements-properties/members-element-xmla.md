---
title: Members-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 89adf68eb4b5c410477f3008a47ad51770393fc2
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="members-element-xmla"></a>Members-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Auflistung von [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) vom übergeordneten Element enthaltenen Elemente [CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CrossProduct>  
   <Members Hierarchy="string">  
      <Member>...</Member>  
   </Members>  
   ...  
</CrossProduct>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md)|  
|Untergeordnete Elemente|[Datenmember](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Hierarchy|Erforderliches **String** -Attribut. Der Name der Hierarchie, der die Elemente, durch enthält, die **Elemente** Element gehören.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Clientanwendung legt die **AxisFormat** Eigenschaft, um *' Clusterformat '*, die Elemente auf jeder Achse in Cluster in der jeder Cluster ein Kreuzprodukt geordneten Mengen an darstellt unterteilt Elemente aus jeder Hierarchie. Jede **Achse** Element besteht aus einem oder mehreren **CrossProduct** Elemente. Jede **CrossProduct** Element enthält eine **Elemente** -Element für jede Hierarchie auf der Achse. Die **Elemente** -Element wiederum enthält ein **Member** -Element für jedes Mitglied in das Kreuzprodukt enthaltenen Hierarchie.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Struktur der **Mitglieder** -Element, wenn ein Client angibt, *' Clusterformat '* für die **AxisFormat** angegebene XMLA-Eigenschaft der folgende Elemente für die Achse:  
  
||||||  
|-|-|-|-|-|  
|**Time**-Hierarchie|1999|1999|2000|2001|  
|**Category**-Hierarchie|Tatsächlich|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size = "4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size = "1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
