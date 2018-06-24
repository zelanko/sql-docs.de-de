---
title: MDDataSet-Datentyp (XMLA) | Microsoft Docs
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
- MDDataSet Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MDDataSet
- MDDataSet
- urn:schemas-microsoft-com:xml-analysis#MDDataSet
helpviewer_keywords:
- MDDataSet data type
ms.assetid: 1a7e0092-f9f0-4ae5-ba27-ad1d8ebe8cb9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 098a123c28e4a449ad6425d1a74ff8355d074e08
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048329"
---
# <a name="mddataset-data-type-xmla"></a>MDDataSet-Datentyp (XMLA)
  Definiert einen abgeleiteten Datentyp, der vom zurückgegebenen mehrdimensionale Daten darstellt, der die [Execute](../xml-elements-methods-execute.md) Methode.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis:mddataset  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <OlapInfo>...</OlapInfo>  
   <Axes>...</Axes>  
   <CellData>...</CellData>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Resultset](resultset-data-type-xmla.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Achsen](../xml-elements-properties/axes-element-xmla.md), [CellData](../xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../xml-elements-properties/olapinfo-element-xmla.md)|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der `MDDataSet`-Datentyp stellt das OLAP-orientierte Rowset (oder Dataset) bereit, das erforderlich ist, um OLAP-Daten in XML darzustellen. Die Inhalte dieses Rowsets können je nach den Werten der variieren die `Content` und `Format` Eigenschaften in der [Eigenschaften](../xml-elements-properties/properties-element-xmla.md) Auflistung von der `Execute` Methode. Weitere Informationen zu den `Content` und `Format` Eigenschaften finden Sie in [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Grundlegende Informationen zu OLE DB für OLAP-Datensatzstrukturen finden Sie unter "MDDataSet-Datentypzuordnung zu OLE DB" in der XML 1.1-Spezifikation (XML for Analysis). Für eine vollständige XML Schema Definition Language (XSD) Stichprobe von der `MDDataSet` -Datentyp, finden Sie unter "Appendix D: MDDataSet Example" in der XML for Analysis 1.1-Spezifikation.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Datentypen &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  