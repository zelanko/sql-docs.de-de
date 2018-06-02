---
title: ConnectionString-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c286aa928195181d5d1b344f71b648510ccceda1
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575842"
---
# <a name="connectionstring-element-xmla"></a>ConnectionString-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Verbindungszeichenfolge, die vom übergeordneten Element verwendeten [Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) oder [Quelle](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|Siehe Tabelle unten.|  
  
|Vorgänger oder übergeordnetes Element|Cardinality|  
|------------------------|-----------------|  
|[Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|1-1: Erforderliches Element, das nur einmal auftritt.|  
|[Quelle](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [Quelle](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Für **Location** -Elemente enthält das **ConnectionString** -Element die Verbindungszeichenfolge, die vom **Restore** - oder **Synchronize** -Befehl entweder zum Aktualisieren einer lokalen Datenquelle oder zum Verbinden mit einer Remoteinstanz verwendet wird.  
  
 Für **Source** -Elemente enthält das **ConnectionString** -Element die Verbindungszeichenfolge, die vom **Synchronize** -Befehl zum Verbinden mit der Quellinstanz verwendet wird.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch
 [Restore-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchronize-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
