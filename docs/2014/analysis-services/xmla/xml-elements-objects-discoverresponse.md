---
title: DiscoverResponse-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscoverResponse Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DiscoverResponse
- microsoft.xml.analysis.discoverresponse
- urn:schemas-microsoft-com:xml-analysis#DiscoverResponse
helpviewer_keywords:
- DiscoverResponse element
ms.assetid: 20e10a82-dbd1-4ead-b92d-f84b4b2f10c6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 763724fb08a849000cb960435847a84447ba5674
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105390"
---
# <a name="discoverresponse-element-xmla"></a>DiscoverResponse-Element (XMLA)
  Enthält die Informationen von einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] als Reaktion auf eine [Discover](xml-elements-methods-discover.md) Methodenaufruf.  
  
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
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[zurück](xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das `DiscoverResponse`-Element ist das oberste Element innerhalb eines Texts der SOAP-Antwort für die `Discover`-Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [ExecuteResponse-Element &#40;XMLA&#41;](xml-elements-objects-executeresponse.md)   
 [Objekte &#40;XMLA&#41;](xml-elements-objects.md)  
  
  
