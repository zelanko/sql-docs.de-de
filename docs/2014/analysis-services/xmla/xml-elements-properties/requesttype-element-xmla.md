---
title: RequestType-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RequestType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RequestType
- urn:schemas-microsoft-com:xml-analysis#RequestType
- microsoft.xml.analysis.requesttype
helpviewer_keywords:
- RequestType element
ms.assetid: 54270a57-e327-4233-b4b2-d85b44652ac5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 322b212853f94a1e1e5b1b48534dee649632d164
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105310"
---
# <a name="requesttype-element-xmla"></a>RequestType-Element (XMLA)
  Bestimmt den Typ des vom zurückgegebenen Metadaten der [Discover](../xml-elements-methods-discover.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Discover>  
   ...  
   <RequestType>...</RequestType>  
   ...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ermitteln](../xml-elements-methods-discover.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das `RequestType`-Element bestimmt das Schemarowset, von dem die `Discover`-Methode Daten zurückgibt. Diese Enumeration ist auf die Namen von unterstützten Schemarowsets beschränkt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Weitere Informationen zu Schemarowsets finden Sie unter [Analysis Services-Schemarowsets](../../schema-rowsets/analysis-services-schema-rowsets.md).  
  
> [!NOTE]  
>  Das `RequestType`-Element listet nur Schemarowsetnamen auf. Ein Fehler tritt auf, wenn die Schemarowset-GUID verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
