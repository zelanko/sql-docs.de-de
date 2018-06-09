---
title: Execute-Methode (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c47a3c1a297bd636c64e52fcb83fda6a2b7bad5
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574932"
---
# <a name="xml-elements---methods---execute"></a>Führen Sie die XML-Elemente - Methoden-
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Sendet XML für Analysis (XMLA) Befehle mit einer Instanz von Analysis Services. Dies schließt Anforderungen im Zusammenhang mit Datenübertragung ein, z. B. das Abrufen oder Aktualisieren von Daten auf dem Server.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
 **SOAP Action** "urn:schemas-microsoft-com:xml-analysis:Execute"  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Befehl](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md), [Parameter](../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md), [Eigenschaften](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die **Execute** -Methode führt XMLA-Befehle, die gemäß der **Befehl** Element und gibt resultierenden Daten entweder mithilfe die XMLA [Rowset](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) -Datentyp (tabellarisches Ergebnis versetzt wird) oder des XMLA- [MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) -Datentyps (für mehrdimensionale Resultsets.)  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel ist ein Beispiel für einen **Execute** -Methodenaufruf, der eine MDX-SELECT-Anweisung (Multidimensional Expressions) enthält.  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>Siehe auch
 [XML-Datentypen &#40;XMLA&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Discover-Methode &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Methoden &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML-Elemente &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Analysis Services-Schemarowsets](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
