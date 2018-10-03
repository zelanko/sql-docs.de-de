---
title: Members-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Members Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Members
- urn:schemas-microsoft-com:xml-analysis#Members
- microsoft.xml.analysis.members
helpviewer_keywords:
- Members element
ms.assetid: 55f9ec3a-5a41-4b3a-acd6-c07598868c46
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa1a418c0dc131f02c1afc2f2dd67810ebf90ea2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083498"
---
# <a name="members-element-xmla"></a>Members-Element (XMLA)
  Enthält eine Auflistung von [Member](member-element-xmla.md) vom übergeordneten Element enthaltenen Elemente [CrossProduct](crossproduct-element-xmla.md) Element.  
  
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
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CrossProduct](crossproduct-element-xmla.md)|  
|Untergeordnete Elemente|[Member](member-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|Hierarchy|Erforderliche `String` Attribut. Der Name der Hierarchie, zu der die Elemente gehören, die im `Members`-Element enthalten sind.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Clientanwendung festlegt der `AxisFormat` Eigenschaft *' Clusterformat '*, die Elemente auf jeder Achse in Cluster, in dem jeder Cluster ein Kreuzprodukt geordneten Mengen an Elementen aus jeder Hierarchie darstellt, unterteilt. Jedes `Axis`-Element besteht aus einem oder mehreren `CrossProduct`-Elementen. Jedes `CrossProduct`-Element enthält ein `Members`-Element für jede Hierarchie auf der Achse. Das `Members`-Element wiederum enthält ein `Member`-Element für jedes Element der im Kreuzprodukt enthaltenen Hierarchie.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Struktur der `Members` -Element, wenn ein Client angibt, *' Clusterformat '* für die `AxisFormat` XMLA-Eigenschaft, wobei die folgenden Elemente für die Achse:  
  
||||||  
|-|-|-|-|-|  
|`Time`-Hierarchie|1999|1999|2000|2001|  
|`Category`-Hierarchie|Tatsächlich|Budget|Budget|Budget|  
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
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
