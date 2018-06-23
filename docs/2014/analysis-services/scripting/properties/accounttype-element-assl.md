---
title: AccountType-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AccountType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff7203d2882689b21a6ab3171880c26a8d385f7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150448"
---
# <a name="accounttype-element-assl"></a>AccountType-Element (ASSL)
  Enthält den Namen des definierten Kontotyps ein [Datenbank](../objects/database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Konto](../objects/account-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Einkommen*|Das Konto ist ein Einnahmenkonto.|  
|*Ausgaben*|Das Konto ist ein Ausgabenkonto.|  
|*Datenfluss*|Das Konto ist ein Cashflowkonto.|  
|*Lastenausgleich*|Das Konto ist ein Bilanzkonto.|  
|*Anlage*|Das Konto ist ein Bestandskonto.|  
|*Haftung*|Das Konto ist ein Passivkonto.|  
|*Statistische*|Das Konto ist ein statistisches Konto.|  
  
 Die Enumeration, die den zulässigen Werten für die entsprechende `AccountType` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>Siehe auch  
 [Accounts-Element &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  