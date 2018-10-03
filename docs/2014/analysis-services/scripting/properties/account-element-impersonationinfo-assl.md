---
title: Konto-Element (ImpersonationInfo) (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Account Element (ImpersonationInfo)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Account element
ms.assetid: aa3a1281-e42a-4926-875b-e6b81f4599c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f454e39a7c4ec4911f38ff070f94fcbe50a34c74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190370"
---
# <a name="account-element-impersonationinfo-assl"></a>Account-Element (ImpersonationInfo) (ASSL)
  Enthält den Namen des Benutzerkontos für den [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) -Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Account>...</Account>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Den Wert des der `Account` Element sowie den Wert des der [Kennwort](password-element-assl.md) -Elements werden zum Zweck des Identitätswechsels verwendet, wenn den Wert des der [ImpersonationMode](impersonationmode-element-assl.md) -Elements für jedes Element abgeleitet der `ImpersonationInfo` Datentyp nastaven NA hodnotu *ImpersonateAccount*.  
  
## <a name="see-also"></a>Siehe auch  
 [DataSourceImpersonationInfo-Element &#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
