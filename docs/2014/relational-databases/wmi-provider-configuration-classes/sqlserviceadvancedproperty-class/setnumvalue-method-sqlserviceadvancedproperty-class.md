---
title: SetNumValue-Methode (SqlServiceAdvancedProperty-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumValue method
ms.assetid: a5e1056b-0b75-4ad6-99c1-89246010d815
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f44d3426d7a3f11157167763e047dcb7423a904f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62635079"
---
# <a name="setnumvalue-method-sqlserviceadvancedproperty-class"></a>SetNumValue-Methode (SqlServiceAdvancedProperty-Klasse)
  Legt den numerischen Wert einer Eigenschaft fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetNumValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein Objekt der [SqlServiceAdvancedProperty-Klasse](sqlserviceadvancedproperty-class.md) , das eine erweiterte Eigenschaft darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*NumValue*|Ein `uint32`-Wert, der den Wert der erweiterten Eigenschaft angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Eigenschaftswert muss numerisch sein, damit die Eigenschaft auf einen numerischen Wert festgelegt werden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
