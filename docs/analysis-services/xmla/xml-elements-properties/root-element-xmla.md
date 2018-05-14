---
title: Root-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f4fc4072c7b19cff327463dd8df8af7d136e6c1e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="root-element-xmla"></a>root-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält ein Ergebnis, das von der [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) -Methode oder einem XMLA-Befehl (XML for Analysis), der über die [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) -Methode ausgeführt wird, zurückgegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<return> <!-- or results-->  
   ...  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">...</root> <!-- for Execute method only -->  
   <!-- or -->  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">...</root>  
   <!-- or -->  
   <root xmlns= xmlns="urn:schemas-microsoft-com:xml-analysis:empty">...</root>  
   ...  
</return>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Siehe Tabelle unten.|  
|Standardwert|Keine|  
|Kardinalität|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
|Ancestor|Datentyp|  
|--------------|---------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[Rowset](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md), [Rowset](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[results](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md), [return](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das **root** -Element enthält die Informationen, die entweder im [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) -Element über einen einzelnen **Discover** -Methodenaufruf oder im [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) -Element über einen einzelnen XMLA-Befehl, der von einem einzelnen **Execute** -Methodenaufruf ausgeführt wurde, zurückgegeben wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
