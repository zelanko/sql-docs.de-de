---
title: AccountType-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5258ff60c8dfafefbf81f87d3538c396c085ccac
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035181"
---
# <a name="accounttype-element-assl"></a>AccountType-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält den Namen des definierten Kontotyps ein [Datenbank](../../../analysis-services/scripting/objects/database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Konto](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Income*|Das Konto ist ein Einnahmenkonto.|  
|*Expense*|Das Konto ist ein Ausgabenkonto.|  
|*Flow*|Das Konto ist ein Cashflowkonto.|  
|*Balance*|Das Konto ist ein Bilanzkonto.|  
|*Asset*|Das Konto ist ein Bestandskonto.|  
|*Liability*|Das Konto ist ein Passivkonto.|  
|*Statistisch*|Das Konto ist ein statistisches Konto.|  
  
 Die Enumeration, die den zulässigen Werten für die entsprechende **AccountType** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>Siehe auch  
 [Accounts-Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
