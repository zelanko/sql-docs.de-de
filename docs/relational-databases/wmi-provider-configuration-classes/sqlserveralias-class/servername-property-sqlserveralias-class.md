---
description: ServerName-Eigenschaft (SqlServerAlias-Klasse)
title: Servername-Eigenschaft (SqlServerAlias)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
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
ms.openlocfilehash: 7a4ef5a8d80f97136bc6313254d07a1a89ffe2ab
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472780"
---
# <a name="servername-property-sqlserveralias-class"></a>ServerName-Eigenschaft (SqlServerAlias-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft den Namen der Instanz von ab, die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] durch den Serververbindungsalias angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ServerName [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlServerAlias-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) , das einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Alias darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgewert, der den Namen der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] angibt, auf die durch den Serververbindungsalias verwiesen wird.  
  
## <a name="remarks"></a>Bemerkungen  
  
