---
title: DataSource-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSource Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSource
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSource
- microsoft.xml.analysis.datasource
helpviewer_keywords:
- DataSource element
ms.assetid: adc0713a-3927-40f3-8b87-012130908f34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3acbba2e1ee5df1535799e133c064b90b6921386
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130525"
---
# <a name="datasource-element-xmla"></a>DataSource-Element (XMLA)
  Enthält eine Out-of-Line-datenquellenbindung für das übergeordnete [Batch](../xml-elements-commands/batch-element-xmla.md) oder [Prozess](../xml-elements-commands/process-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Batch> <!-- or Process>  
...  
   <DataSource>  
      <DatabaseID>...</DatabaseID>  
      <DataSourceID>...</DataSourceID>  
   </DataSource>  
...  
</Batch>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Batch](../xml-elements-commands/batch-element-xmla.md), [Process](../xml-elements-commands/process-element-xmla.md)|  
|Untergeordnete Elemente|[DatabaseID](id-element-xmla.md), [DataSourceID-Wert](datasourceid-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das `DataSource`-Element stellt eine Out-of-Line-Bindung mit einer Datenquelle dar, die vom `Batch` oder `Process`-Befehl eingesetzt wird, um die Datenquellenbindung von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Objekten, die von dem Befehl verarbeitet werden, temporär zu überschreiben.  
  
 Weitere Informationen zur Out-of-Line-Bindungen finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
