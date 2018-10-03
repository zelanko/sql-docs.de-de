---
title: Axis-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Axis Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.axis
- http://schemas.microsoft.com/analysisservices/2003/engine#Axis
helpviewer_keywords:
- Axis element
ms.assetid: 336895e1-4a57-4b43-9a53-e31569866e6c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8587e1cdb0105d72d2bc0219c8d038ca0bd03ca4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153470"
---
# <a name="axis-element-xmla"></a>Axis-Element (XMLA)
  Enthält eine Menge von Tupeln verwendet, um eine einzelne Achse in einem enthaltenen mehrdimensionalen Datasets darstellen einer [Achsen](axes-element-xmla.md) -Element, das verwendet die [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) von zurückgegebener Datentyp die [Execute](../xml-elements-methods-execute.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Axes>  
   ...  
   <Axis> <!-- when AxisFormat XMLA property is set to ClusterFormat -->  
      <CrossProduct>...</CrossProduct>  
   </Axis>  
   <Axis> <!-- when AxisFormat XMLA property is set to TupleFormat or CustomFormat -->  
      <Tuples>...</Tuples>  
   </Axis>  
   ...  
</Axes>  
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
|Übergeordnete Elemente|[Achsen](axes-element-xmla.md)|  
|Untergeordnete Elemente|[CrossProduct](crossproduct-element-xmla.md) oder [Tupel](tuples-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der Inhalt des `Axis`-Elements variiert je nach dem Wert der `AxisFormat`-XMLA-Eigenschaft, die von der `Execute`-Methode verwendet wird.  
  
## <a name="tupleformat"></a>TupleFormat  
 Wenn eine Client-Anwendung legt die `AxisFormat` Eigenschaft *TupleFormat*, wird eine Achse als Menge von Tupeln dargestellt. Jedes `Axis`-Element enthält ein `Tuples`-Element, das die Tupelmenge auf dieser Achse darstellt. Jedes Tupel wird mithilfe eines `Tuple`-Elements dargestellt, das `Member`-Elemente aus jeder Hierarchie auf der Achse enthält.  
  
## <a name="clusterformat"></a>ClusterFormat  
 Wenn eine Clientanwendung festlegt der `AxisFormat` Eigenschaft *' Clusterformat '*, die Elemente auf jeder Achse in Cluster, in dem jeder Cluster ein Kreuzprodukt geordneten Mengen an Elementen aus jeder Hierarchie darstellt, unterteilt. Jedes `Axis`-Element besteht aus einem oder mehreren `CrossProduct`-Elementen. Jedes `CrossProduct`-Element enthält ein `Members`-Element für jede Hierarchie auf der Achse.  
  
## <a name="customformat"></a>CustomFormat  
 Wenn eine Clientanwendung festlegt der `AxisFormat` Eigenschaft *CustomFormat*, ist der Wert behandelt. identisch mit der *TupleFormat* Wert von Analysis Services-Instanz.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Description  
 Das folgende Beispiel veranschaulicht die Struktur der `Axis` Elemente, wenn ein Client *TupleFormat* oder *CustomFormat* für die `AxisFormat` XMLA-Eigenschaft, die gemäß der folgenden Mitglieder für die Achse:  
  
|||||  
|-|-|-|-|  
|`Time`-Hierarchie|1999|1999|2000|  
|`Category`-Hierarchie|Tatsächlich|Budget|Budget|  
  
### <a name="code"></a>Code  
  
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
  
### <a name="description"></a>Description  
 Das folgende Beispiel veranschaulicht die Struktur der `Axis` Elemente, wenn ein Client *' Clusterformat '* für die `AxisFormat` XMLA-Eigenschaft, wobei die folgenden Elemente für die Achse:  
  
||||||  
|-|-|-|-|-|  
|`Time`-Hierarchie|1999|1999|2000|2001|  
|`Category`-Hierarchie|Tatsächlich|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
### <a name="code"></a>Code  
  
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
  
  
