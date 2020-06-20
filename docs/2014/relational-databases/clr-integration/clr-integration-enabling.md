---
title: Aktivieren der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: d7187906f1376deb81ca7ff4770af7b12b63c022
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953670"
---
# <a name="enabling-clr-integration"></a>Aktivieren der CLR-Integration
  Die Funktion zur CLR-Integration (Common Language Runtime) ist standardmäßig deaktiviert und muss aktiviert werden, um Objekte, die mittels CLR-Integration implementiert werden, verwenden zu können. Um die CLR-Integration zu aktivieren, verwenden Sie die Option **CLR-fähig** der gespeicherten Prozedur **sp_configure** :  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 Sie können die CLR-Integration deaktivieren, indem Sie die Option **CLR-fähig** auf 0 festlegen. Wenn Sie die CLR-Integration deaktivieren, stoppt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Ausführung aller CLR-Routinen und entlädt alle Anwendungsdomänen.  
  
> [!NOTE]  
>  Um die CLR-Integration zu aktivieren, müssen Sie über die ALTER SETTINGS-Berechtigung auf Serverebene verfügen, die von Mitgliedern der festen Server Rollen **sysadmin** und **serveradmin** implizit aufbewahrt wird.  
  
> [!NOTE]  
>  Computer, die mit großen Mengen an Arbeitsspeicher und einer großen Anzahl von Prozessoren konfiguriert sind, können das SQL Server-Funktion zur CLR-Integration beim Serverstart möglicherweise nicht laden. Um dieses Problem zu beheben, starten Sie den Server mithilfe der Startoption **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service, und geben Sie einen Wert für den Arbeitsspeicher an, der groß genug ist. Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  CLR (Common Language Runtime) wird beim Lightweightpooling nicht unterstützt. Vor dem Aktivieren der CLR-Integration müssen Sie Lightweightpooling deaktivieren. Weitere Informationen finden Sie unter [Lightweightpooling (Serverkonfigurationsoption)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CLR-fähig (Server Konfigurations Option)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Grant &#40;Transact-SQL-&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [Rollen auf Serverebene](../security/authentication-access/server-level-roles.md)  
  
  
