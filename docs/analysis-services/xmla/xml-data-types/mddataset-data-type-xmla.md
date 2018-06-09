---
title: MDDataSet-Datentyp (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 986fade6d9db3d6170d47181ac960d15febdf260
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573922"
---
# <a name="mddataset-data-type-xmla"></a>MDDataSet-Datentyp (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Definiert einen abgeleiteten Datentyp, der vom zurückgegebenen mehrdimensionale Daten darstellt, der die [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methode.  
  
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
|Basisdatentypen|[Resultset](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Achsen](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md), [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der **MDDataSet** -Datentyp stellt das OLAP-orientierte Rowset (oder Dataset) bereit, das erforderlich ist, um OLAP-Daten in XML darzustellen. Die Inhalte dieses Rowsets können je nach den Werten der variieren die **Content** und **Format** Eigenschaften in der [Eigenschaften](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) Auflistung von der  **Führen Sie** Methode. Weitere Informationen zu den **Content** und **Format** Eigenschaften finden Sie in [XMLA-Eigenschaften unterstützt &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Grundlegende Informationen zu OLE DB für OLAP-Datensatzstrukturen finden Sie unter "MDDataSet-Datentypzuordnung zu OLE DB" in der XML 1.1-Spezifikation (XML for Analysis). Ein vollständiges XSD-Beispiel (XML Schema Definition Language) für den **MDDataSet** -Datentyp finden Sie unter "Appendix D: MDDataSet Example" in der XML 1.1-Spezifikation (XML for Analysis).  
  
## <a name="see-also"></a>Siehe auch
 [XML-Datentypen &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
