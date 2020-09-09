---
description: ExitCode-Eigenschaft (SqlService-Klasse)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 71e5fbe4180c67560709f004ba099bb90ca83b02
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542841"
---
# <a name="exitcode-property-sqlservice-class"></a>ExitCode-Eigenschaft (SqlService-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
