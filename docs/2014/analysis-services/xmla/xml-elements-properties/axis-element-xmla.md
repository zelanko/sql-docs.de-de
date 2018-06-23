---
title: Axis-Element (XMLA) | Microsoft Docs
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
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e30ff03b6e1a58a079d35f8e846ed176c42a3a31
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060554"
---
# <a name="axis-element-xmla"></a>Axis-Element (XMLA)
  Enthält eine Menge von Tupeln, die zur Darstellung einer einzelnen Achse in einer enthaltenen mehrdimensionalen Datasets ein [Achsen](axes-element-xmla.md) Element, das verwendet die [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) von zurückgegebener Datentyp die [Execute](../xml-elements-methods-execute.md) Methode.  
  
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
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Achsen](axes-element-xmla.md)|  
|Untergeordnete Elemente|[CrossProduct](crossproduct-element-xmla.md) oder [Tupel](tuples-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der Inhalt des `Axis`-Elements variiert je nach dem Wert der `AxisFormat`-XMLA-Eigenschaft, die von der `Execute`-Methode verwendet wird.  
  
## <a name="tupleformat"></a>TupleFormat  
 Wenn eine Clientanwendung legt die `AxisFormat` Eigenschaft *' TupleFormat '*, eine Achse wird als eine Menge von Tupeln dargestellt. Jedes `Axis`-Element enthält ein `Tuples`-Element, das die Tupelmenge auf dieser Achse darstellt. Jedes Tupel wird mithilfe eines `Tuple`-Elements dargestellt, das `Member`-Elemente aus jeder Hierarchie auf der Achse enthält.  
  
## <a name="clusterformat"></a>ClusterFormat  
 Wenn eine Clientanwendung legt die `AxisFormat` Eigenschaft, um *' Clusterformat '*, die Elemente auf jeder Achse in Cluster in der jeder Cluster ein Kreuzprodukt geordneten Mengen an Elementen aus jeder Hierarchie darstellt unterteilt. Jedes `Axis`-Element besteht aus einem oder mehreren `CrossProduct`-Elementen. Jedes `CrossProduct`-Element enthält ein `Members`-Element für jede Hierarchie auf der Achse.  
  
## <a name="customformat"></a>CustomFormat  
 Wenn eine Clientanwendung festlegt der `AxisFormat` Eigenschaft *CustomFormat*, wird der Wert behandelt identisch mit der *' TupleFormat '* Wert von einer Analysis Services-Instanz.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Description  
 Das folgende Beispiel veranschaulicht die Struktur der `Axis` Elemente angezeigt, wenn ein Client gibt *' TupleFormat '* oder *CustomFormat* für die `AxisFormat` XMLA-Eigenschaft, die bei Angabe der folgenden Mitglieder für die Achse:  
  
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
 Das folgende Beispiel veranschaulicht die Struktur der `Axis` Elemente angezeigt, wenn ein Client gibt *' Clusterformat '* für die `AxisFormat` XMLA-Eigenschaft, wobei die folgenden Elemente für die Achse:  
  
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
  
  