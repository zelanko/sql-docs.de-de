---
title: ImpersonationMode-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ImpersonationMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ImpersonateMode
helpviewer_keywords:
- ImpersonateMode element
ms.assetid: 160fdcb2-ac9f-4c5a-a0eb-a5f7669166b9
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e41e5b5fef7759f6ad310a7f04dc012a7b7cb54f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149506"
---
# <a name="impersonationmode-element-assl"></a>ImpersonationMode-Element (ASSL)
  Enthält einen Wert, der die Methode des Identitätswechsels für Elemente, die angibt von der abgeleiteten der [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) -Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ImpersonationInfo>  
   ...  
   <ImpersonationMode>...</ImpersonationMode>  
  
</ImpersonationInfo>...  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Standardwert*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Standardwert*|Das übergeordnete Element verwendet die Identitätswechselmethode, die für den Kontext, in dem der Identitätswechsel verwendet wird, geeignet ist.|  
|*ImpersonateAccount*|Das übergeordnete Element verwendet die Anmeldeinformationen des Benutzerkontos, das im übergeordneten Element angegeben ist.|  
|*ImpersonateAnonymous*|Das übergeordnete Element verwendet die Anmeldeinformationen eines anonymen Benutzers.|  
|*ImpersonateCurrentUser*|Das übergeordnete Element verwendet die Anmeldeinformationen des aktuellen Benutzers.|  
|*Konfiguriert ImpersonateServiceAccount*|Das übergeordnete Element verwendet die Anmeldeinformationen des Dienstkontos, das mit der Instanz verknüpft ist [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `ImpersonationMode` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ImpersonationLevel>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  