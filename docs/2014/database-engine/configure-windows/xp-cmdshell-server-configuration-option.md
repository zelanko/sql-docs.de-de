---
title: xp_cmdshell (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 647516b851ad8d7a6716e49d5589adb2681fe541
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252752"
---
# <a name="xpcmdshell-server-configuration-option"></a>xp_cmdshell (Serverkonfigurationsoption)
  Die **xp_cmdshell** -Option ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Serverkonfigurationsoption, mit der Systemadministratoren steuern können, ob auf einem System die erweiterte gespeicherte Prozedur **xp_cmdshell** ausgeführt werden kann. Die Option **xp_cmdshell** ist in neuen Installationen standardmäßig deaktiviert. Sie kann mithilfe der richtlinienbasierten Verwaltung oder durch Ausführen der gespeicherten Systemprozedur **sp_configure** aktiviert werden, wie im folgenden Beispiel dargestellt:  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
