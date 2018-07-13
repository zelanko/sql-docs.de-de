---
title: Properties-Element (XMLA) | Microsoft-Dokumentation
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
- Properties Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Properties
- microsoft.xml.analysis.properties
- urn:schemas-microsoft-com:xml-analysis#Properties
- Properties
helpviewer_keywords:
- Properties element
ms.assetid: 0b5468e5-bf23-4d22-862f-72e27a9fff2f
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 99cb1b43ad7629fd87759d5ea724e068319152b8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237230"
---
# <a name="properties-element-xmla"></a>Properties-Element (XMLA)
  Enthält XML-Code für die Eigenschaften des Analysis (XMAL) ein, die die [Discover](../xml-elements-methods-discover.md) und [Execute](../xml-elements-methods-execute.md) Methoden.  
  
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
|Übergeordnete Elemente|[Entdecken Sie](../xml-elements-methods-discover.md), [ausführen](../xml-elements-methods-execute.md)|  
|Untergeordnete Elemente|[PropertyList](propertylist-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Properties` -Element stellt dar, XMLA-Eigenschaften, um Aspekte der steuern die `Discover` und `Execute` Methoden, z. B. das Definieren von Informationen, die für die Verbindung zum Angeben des rückgabeformats des Resultsets oder das Angeben der Datenquelle erforderlich sind das Gebietsschema, in dem die Daten formatiert werden soll.  
  
 Die verfügbaren Eigenschaften und deren Werte erhalten Sie mithilfe des Anforderungstyps DISCOVER_PROPERTIES mit der `Discover` Methode.  
  
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
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
