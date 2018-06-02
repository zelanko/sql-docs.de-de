---
title: DiscoverResponse-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9ad13a08b6afa19b59dbdaf8d43686c13649a43
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574345"
---
# <a name="xml-elements---objects---discoverresponse"></a>XML-Elemente - Objekte - DiscoverResponse
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält die Informationen von einer Instanz von Analysis Services als Antwort auf eine [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) -Methodenaufruf.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DiscoverResponse>  
   <return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Rückgabewert](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das **DiscoverResponse** -Element ist das oberste Element innerhalb eines Texts der SOAP-Antwort für die **Discover** -Methode.  
  
## <a name="see-also"></a>Siehe auch
 [ExecuteResponse-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)   
 [Objekte &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  
