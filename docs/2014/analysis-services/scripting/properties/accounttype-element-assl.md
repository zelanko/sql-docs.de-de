---
title: AccountType-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c412993422eb963265f99274544ce6f673d5ad9a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075980"
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
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Konto](../objects/account-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Einkommen*|Das Konto ist ein Einnahmenkonto.|  
|*Ausgaben*|Das Konto ist ein Ausgabenkonto.|  
|*Flow*|Das Konto ist ein Cashflowkonto.|  
|*Lastenausgleich*|Das Konto ist ein Bilanzkonto.|  
|*Asset*|Das Konto ist ein Bestandskonto.|  
|*Haftung*|Das Konto ist ein Passivkonto.|  
|*Statistische*|Das Konto ist ein statistisches Konto.|  
  
 Die Enumeration, der den zulässigen Werten für `AccountType` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>Siehe auch  
 [Konten Element &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
