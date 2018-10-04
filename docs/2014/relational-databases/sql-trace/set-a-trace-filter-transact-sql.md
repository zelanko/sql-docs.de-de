---
title: SetBoolValue-Methode (SqlServiceAdvancedProperty-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2edfd80e8b143e9e8b48ca34b979506b27be35ce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196390"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a>SetBoolValue-Methode (SqlServiceAdvancedProperty-Klasse)
  Legt den booleschen Wert einer Eigenschaft fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetBoolValue [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein Objekt der [SqlServiceAdvancedProperty-Klasse](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , das eine erweiterte Eigenschaft darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*BoolValue*|Ein boleescher Wert, der den Wert der erweiterten Eigenschaft angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32` -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert 1, wenn die Anforderung nicht unterstützt wird, wurde, und jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
 Der Eingenschaftswert muss ein boolescher Wert sein, damit die Eigenschaft auf einen boleeschen Wert festgelegt werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
