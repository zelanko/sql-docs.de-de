---
title: ExecuteResponse-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ExecuteResponse Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ExecuteResponse
- http://schemas.microsoft.com/analysisservices/2003/engine#ExecuteResponse
- microsoft.xml.analysis.executeresponse
helpviewer_keywords:
- ExecuteResponse element
ms.assetid: 6edb1b82-da4c-4cd9-9385-bea04032f0eb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 002da257a4d1137b0e52743eec99f1b0aced56c0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48047581"
---
# <a name="executeresponse-element-xmla"></a>ExecuteResponse-Element (XMLA)
  Enthält die Informationen von einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] als Reaktion auf eine [Execute](xml-elements-methods-execute.md) Methodenaufruf.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ExecuteResponse>  
   <return>  
</ExecuteResponse>  
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
 Das `ExecuteResponse`-Element ist das oberste Element innerhalb eines Texts der SOAP-Antwort für die `Execute`-Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [DiscoverResponse-Element &#40;XMLA&#41;](xml-elements-objects-discoverresponse.md)   
 [Objekte &#40;XMLA&#41;](xml-elements-objects.md)  
  
  
