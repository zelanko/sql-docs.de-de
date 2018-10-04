---
title: AliasName-Eigenschaft (SqlServerAlias-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- AliasName Property (SqlServerAlias Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- AliasName property
ms.assetid: 5c4c88f3-c1cf-471a-9d91-f47657933e2f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 53c50db2baeeb894f41cf84274af3e7f7a24699b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776878"
---
# <a name="aliasname-property-sqlserveralias-class"></a>AliasName-Eigenschaft (SqlServerAlias-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Namen des Serververbindungsalias ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.AliasName [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlServerAlias-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) , das einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Alias darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Wert des Typs **string** , der den Namen des Serververbindungsalias angibt.  
  
## <a name="remarks"></a>Hinweise  
  
