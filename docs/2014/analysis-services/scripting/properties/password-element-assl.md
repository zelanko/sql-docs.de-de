---
title: Password-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Password element
ms.assetid: ee756b01-fb08-4a9a-8c2a-7c04af0f8658
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fcaf2b19e885577559d00337349d77cb8f732fcb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224790"
---
# <a name="password-element-assl"></a>Password-Element (ASSL)
  Enthält das Kennwort des Benutzerkontos für den [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Password>...</Password>  
   ...  
</ImpersonationInfo>  
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
|Übergeordnetes Element|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Den Wert des der `Password` Element sowie den Wert des der [Konto](account-element-impersonationinfo-assl.md) -Elements werden zum Zweck des Identitätswechsels verwendet, wenn den Wert des der [ImpersonationMode](impersonationmode-element-assl.md) -Elements für jedes Element abgeleitet der `ImpersonationInfo` Datentyp nastaven NA hodnotu *ImpersonateAccount*.  
  
 Nur Mitglieder der Serveradministratorrolle für die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz bieten einen leeren Wert für die `Password` Element  
  
## <a name="see-also"></a>Siehe auch  
 [DataSourceImpersonationInfo-Element &#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
