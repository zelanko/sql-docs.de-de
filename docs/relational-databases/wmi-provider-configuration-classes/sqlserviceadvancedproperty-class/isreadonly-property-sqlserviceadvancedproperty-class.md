---
title: Isread only-Eigenschaft (SqlServiceAdvancedProperty)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- IsReadOnly Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- IsReadOnly property
ms.assetid: 9672e70f-1d8c-4133-ac73-3b5733a1c4ee
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1324d352ca113a441dc388a235d44b5274e441be
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73658983"
---
# <a name="isreadonly-property-sqlserviceadvancedproperty-class"></a>IsReadOnly-Eigenschaft (SqlServiceAdvancedProperty-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft die boolesche Eigenschaft ab, die angibt, ob die erweiterte Eigenschaft schreibgeschützt ist, oder legt diese fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.IsReadOnly [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein Objekt der [SqlServiceAdvancedProperty-Klasse](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , das eine erweiterte Eigenschaft darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boleescher Wert, der angibt, ob die erweiterte Eigenschaft schreibgeschützt ist oder nicht: **true** , wenn die erweiterte Eigenschaft schreibgeschützt ist, bzw. **false** , wenn die erweiterte Eigenschaft geändert werden kann.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
