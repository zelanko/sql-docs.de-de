---
title: ImpersonationInfoSecurity-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ImpersonationInfoSecurity Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ImpersonationInfoSecurity element
ms.assetid: 583fec36-90ef-4d6a-9888-ece6ae865c53
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4aaf5aee83f6aa6102aeeb9488ddb7a75c4af540
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224906"
---
# <a name="impersonationinfosecurity-element-assl"></a>ImpersonationInfoSecurity-Element (ASSL)
  Enthält einen schreibgeschützten Wert, der angibt, ob die Sicherheitsanmeldeinformationen, die im bereitgestellt werden, Änderungen vorgenommen wurden die [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) -Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ImpersonationInfo>  
   ...  
   <ImpersonationInfoSecurity>...</ImpersonationInfoSecurity>  
  
</ImpersonationInfo>...  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*PasswordRemoved*|Kennwortinformationen wurden aus den angegebenen Sicherheitsanmeldeinformationen entfernt.|  
|*unverändert*|Keine Änderungen wurden an den angegebenen Sicherheitsanmeldeinformationen vorgenommen.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `ImpersonationInfoSecurity` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ImpersonationInfoSecurity>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
