---
description: SqlServerAlias-Klasse
title: SqlServerAlias-Klasse
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- SqlServerAlias Class
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a1609867cc1b21338ce20deab1d51302cebde201
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472749"
---
# <a name="sqlserveralias-class"></a>SqlServerAlias-Klasse
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Die [SqlServerAlias Class](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) -Klasse stellt einen Serververbindungsalias dar.  
  
 Ein Serververbindungsalias ist erforderlich, wenn beide der folgenden Situationen eintreten:  
  
-   Der Client stellt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über einen Netzwerk Transport, der nicht der standardmäßige Netzwerk Transport ist, eine Verbindung mit einer Instanz von her.  
  
-   Die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , mit der der Client verbunden ist, überwacht einen anderen Named Pipe.  
  
 **Hinweis:** Die [SqlServerAlias-Klasse](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) erbt die **Put** -Methode von der Provider-Klasse. Es werden jedoch keine Ergebnisse ausgegeben , wie von der **Provider::Put** -Methode angegeben. Weitere Informationen finden Sie in der WMI-Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
