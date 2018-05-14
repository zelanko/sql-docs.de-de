---
title: CellData-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01f1bfbd4565c42f4867a781b8f4502ede3a09f4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="celldata-element-xmla"></a>CellData-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Liste von Zellelementen, die die Zellendaten darstellen, die in einem [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) -Element enthalten sind, das den [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) -Datentyp verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <CellData>  
      <Cell>...</Cell>  
   </CellData>  
</root>  
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
|Übergeordnete Elemente|[Stamm](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Untergeordnete Elemente|[Zelle](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Im übergeordneten "root"-Element folgt auf das **Axes** -Element das **CellData** -Element, eine Auflistung von **Cell** -Elementen, die die Zelleigenschaftswerte für jede im mehrdimensionalen Dataset verwendete Zelle enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
