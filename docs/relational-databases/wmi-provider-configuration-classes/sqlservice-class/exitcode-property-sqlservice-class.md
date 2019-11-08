---
title: ExitCode-Eigenschaft (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ExitCode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 392fc529b10e79d96a83ccd896733d14d0b8b4dc
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73659681"
---
# <a name="exitcode-property-sqlservice-class"></a>ExitCode-Eigenschaft (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32-Fehlercode ab, der beim Starten und Beenden des Diensts aufgetretene Probleme definiert, oder legt diesen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ExitCode [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der den Exitcode angibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft wird auf ERROR_SERVICE_SPECIFIC_ERROR (1066) festgelegt, wenn der Fehler eindeutig in Bezug auf den Dienst ist, der durch diese Klasse dargestellt wird. Vom Dienst wird dieser Wert bei der Ausführung und erneut bei normaler Beendigung auf NO_ERROR festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
