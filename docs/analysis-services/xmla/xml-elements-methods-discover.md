---
title: Discover-Methode (XMLA) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 921afc6d17a0eddcba48e5a6a6064810a3b3b6ef
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575012"
---
# <a name="xml-elements---methods---discover"></a>XML-Elemente - Methoden - Ermittlung
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Ruft die Informationen, z. B. die Liste der verfügbaren Datenbanken oder Details zu einem bestimmten Objekt von einer Instanz von Analysis Services ab. Die mit der **Discover** -Methode abgerufenen Daten hängen von den Werten der an sie übergebenen Parameter ab.  
  
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
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Eigenschaften](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md), [RequestType](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md), [Einschränkungen](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die **Discover** -Methode fordert Metadaten über Instanzen und Objekten. Metadaten werden zurückgegeben, mit dem XMLA [Rowset](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) -Datentyp.  
 
> [!TIP] 
> Wenn Sie mit XML-Befehle nicht vertraut sind, klicken Sie auf die XMLA-Abfrage-Vorlage die **Abfrage** Symbolleiste in Management Studio, erstellen Sie die Abfrage, und fügen Sie Parameter hinzu. Weitere Informationen finden Sie unter [Use Analysis Services Templates in SQL Server Management Studio](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md). 
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel sendet der Client die **Discover** Aufruf zum Anfordern einer Liste von Cubes von der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Analysis Services-Beispieldatenbank:  
  
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
 [XML-Datentypen &#40;XMLA&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Execute-Methode &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [Methoden &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML-Elemente &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Analysis Services-Schemarowsets](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
