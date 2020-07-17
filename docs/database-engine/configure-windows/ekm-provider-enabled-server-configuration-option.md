---
title: EKM provider enabled (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Informationen zur Option „EKM provider enabled“ Diese Option steuert die EKM-Geräteunterstützung (Extensible Key Management, erweiterbare Schlüsselverwaltung) in SQL Server. Hier erfahren Sie, wie Sie diese Option aktivieren oder deaktivieren.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- external encryption provider
helpviewer_keywords:
- EKM provider enabled option
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
author: markingmyname
ms.author: maghan
ms.openlocfilehash: be9e074cd3d58571a0db9646648207b26b1512b3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772512"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a>EKM provider enabled (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die Option **EKM provider enabled** steuert die EKM-Geräteunterstützung (Extensible Key Management, erweiterbare Schlüsselverwaltung) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diese Option ist standardmäßig deaktiviert.  
  
 Führen Sie einen der folgenden **sp_configure** -Befehle aus, um die Funktion zu aktivieren bzw. zu deaktivieren:  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]
>  Diese Option ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  

