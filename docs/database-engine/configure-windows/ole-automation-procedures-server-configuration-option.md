---
title: OLE-Automatisierungsprozeduren (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Option „OLE-Automatisierungsprozeduren“. Sie erfahren, wie die Option festlegt, ob SQL Server OLE-Automatisierungsobjekte in Transact-SQL-Batches instanziieren kann.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5390fce7517b56ea26a33392a72da7cb39dcd34d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773683"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>OLE-Automatisierungsprozeduren (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Verwenden Sie die **OLE-Automatisierungsprozeduren** -Option, um anzugeben, ob OLE-Automatisierungsobjekte in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Batches instantiiert werden können. Diese Option kann auch mithilfe der richtlinienbasierten Verwaltung oder der gespeicherten Prozedur **sp_configure** konfiguriert werden. Weitere Informationen finden Sie unter [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md).  
  
 Die **Ole Automation Procedures** -Option kann auf die folgenden Werte festgelegt werden.  
  
 0  
 OLE-Automatisierungsprozeduren sind deaktiviert. Standardeinstellung für neue Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 OLE-Automatisierungsprozeduren sind aktiviert.  
  
 Wenn OLE-Automatisierungsprozeduren aktiviert sind, startet ein Aufruf von **sp_OACreate** die freigegebene OLE-Ausführungsumgebung.  
  
 Der aktuelle Wert der **OLE-Automatisierungsprozeduren** -Option kann mithilfe der gespeicherten Systemprozedur **sp_configure** angezeigt und geändert werden.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie die aktuelle Einstellung von OLE-Automatisierungsprozeduren angezeigt werden kann.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 Das folgende Beispiel zeigt, wie OLE-Automatisierungsprozeduren aktiviert werden.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
