---
title: Members-Element (XMLA) | Microsoft-Dokumentation
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
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 37eb0532f56fd4aff8ca760b843697f30f3c9585
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201960"
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
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
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
  
  
