---
title: ServerName-Eigenschaft (SqlServerAlias-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- ServerName Property (SqlServerAlias Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ServerName property
ms.assetid: 58c82b19-b548-42fa-9c5a-059b606da097
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5319f26db7b54fa6bb5bcae73068c7f11e17362d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47768378"
---
# <a name="servername-property-sqlserveralias-class"></a>ServerName-Eigenschaft (SqlServerAlias-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Namen der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab, die durch den Serververbindungsalias angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ServerName [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlServerAlias-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) , das einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Alias darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgewert, der den Namen der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] angibt, auf die durch den Serververbindungsalias verwiesen wird.  
  
## <a name="remarks"></a>Hinweise  
  
