---
title: PropertyList-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49dad8f88ffb9fb517492ad7920ac1a260e1a912
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="propertylist-element-xmla"></a>PropertyList-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Auflistung von XML für Analysis (XMLA)-Eigenschaften, die verwendet werden, indem Sie die [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) und [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methoden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Properties>  
   <PropertyList>  
      <!-- Zero or more XMLA properties -->  
   </PropertyList>  
</Properties>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Eigenschaften](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
|Untergeordnete Elemente|XMLA-Eigenschaften (siehe Hinweise)|  
  
## <a name="remarks"></a>Hinweise  
 Das **PropertyList** -Element enthält eine Auflistung von XMLA-Eigenschaften. Jede Eigenschaft ermöglicht dem Benutzer, einige Aspekte der **Discover** -Methode und der **Execute** -Methode zu steuern. Dazu gehört das Definieren von Informationen, die für die Verbindung mit der Datenquelle erforderlich sind, das Angeben des Rückgabeformats des Resultsets oder das Angeben des Gebietsschemas, für das die Daten formatiert werden sollen. Jede XMLA-Eigenschaft im **PropertyList** -Element wird durch ein separates XML-Element definiert. Beim Wert der XMLA-Eigenschaft handelt es sich um die Daten, die im XML-Element enthalten sind. Der Name der XMLA-Eigenschaft entspricht dem Namen des XML-Elements.  
  
 Die benötigten Eigenschaften und ihre Werte können über eine Nutzung des Anforderungstyps DISCOVER_PROPERTIES mit der **Discover** -Methode abgerufen werden. Es gibt keine erforderliche Reihenfolge für die im **PropertyList** -Element aufgelisteten Eigenschaften.  
  
 Weitere Informationen zu den XMLA-Eigenschaften, die von unterstützt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], finden Sie unter [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
