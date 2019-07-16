---
title: ProcessId-Klasse (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProcessId Class (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d6e523c7f0037c027cafc27651cd131614c314c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68120000"
---
# <a name="processid-class-sqlservice-class"></a>ProcessId-Klasse (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft die Systemprozess-ID ab, die einen Dienst eindeutig identifiziert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ProcessId [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der die ID zur eindeutigen Kennzeichnung des Prozesses angibt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
