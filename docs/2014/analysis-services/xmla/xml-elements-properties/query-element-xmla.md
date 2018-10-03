---
title: Abfrage-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Query Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Query
- microsoft.xml.analysis.query
- http://schemas.microsoft.com/analysisservices/2003/engine#Query
helpviewer_keywords:
- Query element
ms.assetid: 5a4544e4-012f-4a47-942c-23596400ea16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 68da02ef99a5668c7ee0a3a57a06aca90ae68a25
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224400"
---
# <a name="query-element-xmla"></a>Query-Element (XMLA)
  Enthält eine Abfrage innerhalb der [Abfragen](queries-element-xmla.md) Auflistung für die [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md) -Befehl während verwendungsbasierter Optimierung.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Queries>  
   ...  
   <Query>...</Query>  
   ...  
</Queries>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Abfragen](queries-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der `DesignAggregations`-Befehl unterstützt verwendungsbasierte Optimierung durch die Einbindung ein oder mehrerer `Query`-Elemente in die `Queries`-Auflistung des Befehls. Jede `Query` -Element stellt dar, eine Zielabfrage, die der Entwurfsprozess nutzt, um Aggregationen zu definieren, die am häufigsten verwendeten Abfragen abzielen. Sie können entweder Ihre eigenen zielabfragen festlegen oder können Sie die Informationen gespeichert, die von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] im Abfrageprotokoll einbezogen, die zum Abrufen von Informationen über die am häufigsten verwendeten Abfragen.  
  
 Wenn Sie Aggregationen iterativ entwerfen, nur müssen Sie zielabfragen im ersten übergeben `DesignAggregations` Befehl, weil die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz diese zielabfragen speichert und verwendet Sie diese Abfragen, während der nachfolgenden `DesignAggregations` Befehle. Nachdem Sie Zielabfragen im ersten `DesignAggregations`-Befehl eines iterativen Prozesses weitergegeben haben, generiert jeder darauf folgende `DesignAggregations`-Befehl, der über Zielabfragen in der `Queries`-Eigenschaft verfügt, einen Fehler.  
  
 Das `Query`-Element enthält einen durch Trennzeichen getrennten Wert, der die folgenden Argumente beinhaltet:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Häufigkeit*  
 Ein Gewichtungsfaktor, der der Anzahl der Male entspricht, die eine Abfrage zuvor ausgeführt wurde. Wenn die `Query` -Element stellt dar, eine neue Abfrage, die *Häufigkeit* den Gewichtungsfaktor an, die der Entwurfsprozess für die Evaluierung der Abfrage darstellt. Bei steigendem Häufigkeitswert, steigt die Gewichtung auf die Abfrage während des Entwurfsprozesses.  
  
 *DataSet*  
 Eine numerische Zeichenfolge, die festlegt, welche Attribute einer Dimension in die Abfrage eingebunden werden. Diese Zeichenfolge muss die gleiche Anzahl an Zeichen wie die Anzahl an Attributen in der Dimension haben. null (0) zeigt an, dass das Attribut an der angegebenen Ordnungsposition für die angegebene Dimension nicht in der Abfrage enthalten ist. Eins (1) zeigt an, dass das Attribut an der angegebenen Ordnungsposition für die angegebene Dimension in der Abfrage enthalten ist.  
  
 Beispielsweise bezieht sich die Zeichenfolge "011" auf eine Abfrage mit einer Dimension mit drei Attributen, von denen das zweite und dritte Attribut in der Abfrage enthalten sind.  
  
> [!NOTE]  
>  Einige Attribute sind von der Berücksichtigung im Dataset ausgenommen. Weitere Informationen über ausgenommene Attribute finden Sie unter [Eigenschaften (XMLA)](query-element-xmla.md).  
  
 Jede Dimension in der Measuregruppe, die den Aggregationsentwurf enthält, wird durch dargestellt eine *Dataset* Wert in der `Query` Element. Die Reihenfolge der *Dataset* -Werte muss der Reihenfolge der Dimensionen entsprechen, die in die Measuregruppe eingebunden sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen von Aggregationen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
