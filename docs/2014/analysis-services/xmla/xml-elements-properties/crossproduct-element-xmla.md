---
title: CrossProduct-Element (XMLA) | Microsoft-Dokumentation
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
- CrossProduct Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CrossProduct
- microsoft.xml.analysis.crossproduct
- urn:schemas-microsoft-com:xml-analysis#CrossProduct
helpviewer_keywords:
- CrossProduct element
ms.assetid: a9a1584e-d2dd-45db-a918-d694c20d8189
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0d76cc463d39a3b33de41f1c342f5d9f8f800bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278226"
---
# <a name="crossproduct-element-xmla"></a>CrossProduct-Element (XMLA)
  Enthält ein Kreuzprodukt geordneten Mengen an Elementen aus jeder Hierarchie für eine [Achse](axis-element-xmla.md) -Element, das verwendet die [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) von zurückgegebener Datentyp die [Execute](../xml-elements-methods-execute.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Axis>  
   ...  
   <CrossProduct Size="integer">  
      <Members>...</Members>  
   </CrossProduct>  
   ...  
</Axis>  
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
|Übergeordnete Elemente|[Axis](axis-element-xmla.md)|  
|Untergeordnete Elemente|[Elemente](members-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|Größe|Erforderliche `Integer` Attribut. Gibt die Anzahl von Tupeln an, die im durch das `CrossProduct`-Element dargestellten Kreuzprodukt enthalten sind.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Clientanwendung festlegt der `AxisFormat` Eigenschaft *' Clusterformat '*, die Elemente auf jeder Achse in Cluster, in dem jeder Cluster ein Kreuzprodukt geordneten Mengen an Elementen aus jeder Hierarchie darstellt, unterteilt. Jeder Cluster wird durch ein `CrossProduct`-Element dargestellt. Jedes `CrossProduct`-Element enthält ein `Members`-Element für jede Hierarchie auf der Achse. Ein `CrossProduct`-Element kann Elemente einer einzelnen Hierarchie enthalten.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Struktur der `CrossProduct` -Element, wenn ein Client angibt, *' Clusterformat '* für die `AxisFormat` XMLA-Eigenschaft, wobei die folgenden Elemente für die Achse:  
  
||||||  
|-|-|-|-|-|  
|`Time`-Hierarchie|1999|1999|2000|2001|  
|`Category`-Hierarchie|Tatsächlich|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size="4">  
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
      <CrossProduct Size="1">  
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
  
  
