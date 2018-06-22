---
title: Execute-Methode (XMLA) | Microsoft Docs
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
- Execute Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords:
- Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
caps.latest.revision: 34
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5c32261e06788f366a6c5ce5af24c508b87a6882
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049261"
---
# <a name="execute-method-xmla"></a>Execute-Methode (XMLA)
  Sendet XML für Analysis (XMLA) Befehle mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Dies schließt Anforderungen im Zusammenhang mit Datenübertragung ein, z. B. das Abrufen oder Aktualisieren von Daten auf dem Server.  
  
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
|Untergeordnete Elemente|[Befehl](xml-elements-properties/command-element-xmla.md), [Parameter](xml-elements-properties/parameters-element-xmla.md), [Eigenschaften](xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Execute` -Methode führt XMLA-Befehle, die gemäß der `Command` Element und gibt resultierenden Daten entweder mithilfe die XMLA [Rowset](xml-data-types/rowset-data-type-xmla.md) -Datentyp (für tabellarische Resultsets) oder des XMLA- [MDDataSet](xml-data-types/mddataset-data-type-xmla.md) -Datentyps (für mehrdimensionale Resultsets.)  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird ein Beispiel für eine `Execute` -Methodenaufruf, der eine SELECT-Anweisung von MDX (Multidimensional Expressions) enthält.  
  
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
 [XML-Datentypen &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Discover-Methode &#40;XMLA&#41;](xml-elements-methods-discover.md)   
 [Methoden &#40;XMLA&#41;](xml-elements-methods.md)   
 [XML-Elemente &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Analysis Services-Schemarowsets](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  