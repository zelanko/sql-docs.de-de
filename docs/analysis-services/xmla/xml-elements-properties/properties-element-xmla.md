---
title: Properties-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c72d367944a79e86d9bfa251121e8589cbc0e86
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576122"
---
# <a name="properties-element-xmla"></a>Properties-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält XML für Analysis (XMAL)-Eigenschaften, die verwendet werden, indem Sie die [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) und [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methoden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Discover> <!-- or Execute -->  
...  
   <Properties>  
      <PropertyList>...</PropertyList>  
   </Properties>  
...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ermitteln](../../../analysis-services/xmla/xml-elements-methods-discover.md), [ausführen](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Untergeordnete Elemente|[PropertyList](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das **Properties** -Element repräsentiert XMLA-Eigenschaften, mit denen Aspekte der **Discover** -Methode und der **Execute** -Methode gesteuert werden. Dazu gehört das Definieren von Informationen, die für die Verbindung mit der Datenquelle erforderlich sind, das Angeben des Rückgabeformats des Resultsets oder das Angeben des Gebietsschemas, für das die Daten formatiert werden sollen.  
  
 Die benötigten Eigenschaften und ihre Werte können über eine Nutzung des Anforderungstyps DISCOVER_PROPERTIES mit der **Discover** -Methode abgerufen werden.  
  
## <a name="example"></a>Beispiel  
  
```  
<Properties>  
   <PropertyList>  
      <DataSourceInfo>  
         Provider=MSOLAP;Data Source=local;  
      </DataSourceInfo>  
      <Catalog>  
         Foodmart 2000  
      </Catalog>  
      <Format>  
         Multidimensional  
      </Format>  
   </PropertyList>  
</Properties>  
```  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
