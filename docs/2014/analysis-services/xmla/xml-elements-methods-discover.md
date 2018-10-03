---
title: Discover-Methode (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Discover Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.discover
- urn:schemas-microsoft-com:xml-analysis#Discover
- Discover
helpviewer_keywords:
- Discover method
ms.assetid: 0eb52d88-c081-416e-a229-610e4373b0b3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 91ea30a495eb76c22075007f48e3ae721504ef49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116320"
---
# <a name="discover-method-xmla"></a>Discover-Methode (XMLA)
  Ruft Informationen wie die Liste der verfügbaren Datenbanken oder die Details zu einem bestimmten Objekt von einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Die Daten abgerufen werden, mit der `Discover` Methode hängt von der Werte der Parameter übergeben.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
 **SOAP Action** "urn:schemas-microsoft-com:xml-analysis:Discover"  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Discover>  
   <RequestType>...</RequestType>  
   <Restrictions>...</Restrictions>  
   <Properties>...</Properties>  
</Discover>  
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
|Übergeordnetes Element|None|  
|Untergeordnete Elemente|[Eigenschaften](xml-elements-properties/properties-element-xmla.md), [RequestType](xml-elements-properties/type-element-xmla.md), [Einschränkungen](xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Discover` -Methode fordert Metadaten über [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanzen und Objekten. Metadaten werden zurückgegeben, mit dem XMLA [Rowset](xml-data-types/rowset-data-type-xmla.md) -Datentyp.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel sendet der Client die `Discover` Aufruf zum Anfordern einer Liste von Cubes von der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Beispiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank:  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>MDSCHEMA_CUBES</RequestType>  
   <Restrictions>  
      <RestrictionList>  
         <CATALOG_NAME>Adventure Works DW Multidimensional 2012</CATALOG_NAME>  
      </RestrictionList>  
   </Restrictions>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Tabular</Format>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Datentypen &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Execute-Methode &#40;XMLA&#41;](xml-elements-methods-execute.md)   
 [Methoden &#40;XMLA&#41;](xml-elements-methods.md)   
 [XML-Elemente &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Analysis Services-Schemarowsets](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
