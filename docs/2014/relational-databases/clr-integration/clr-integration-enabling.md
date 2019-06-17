---
title: Aktivieren der Clrintegration | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 1cb5f1f4bcc3a3e796cc99b4da7f14e5a5976b93
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62874104"
---
# <a name="enabling-clr-integration"></a>Aktivieren der CLR-Integration
  Die Funktion zur CLR-Integration (Common Language Runtime) ist standardmäßig deaktiviert und muss aktiviert werden, um Objekte, die mittels CLR-Integration implementiert werden, verwenden zu können. Verwenden Sie zum Aktivieren der CLR-Integration die **Clr-fähig** Möglichkeit, die **Sp_configure** gespeicherte Prozedur:  
  
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
  
 Sie können die CLR-Integration deaktivieren, indem die **Clr-fähig** auf 0. Wenn Sie die CLR-Integration deaktivieren, stoppt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Ausführung aller CLR-Routinen und entlädt alle Anwendungsdomänen.  
  
> [!NOTE]  
>  Um CLR-Integration zu aktivieren, benötigen Sie ALTER SETTINGS Serverberechtigung, die implizit Mitglieder erhalten die **Sysadmin** und **Serveradmin** festen Serverrollen.  
  
> [!NOTE]  
>  Computer, die mit großen Mengen an Arbeitsspeicher und einer großen Anzahl von Prozessoren konfiguriert sind, können das SQL Server-Funktion zur CLR-Integration beim Serverstart möglicherweise nicht laden. Um dieses Problem zu beheben, starten Sie den Server mithilfe der **-Gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Startoption, und geben Sie einen Speicherwert, der groß genug ist. Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  CLR (Common Language Runtime) wird beim Lightweightpooling nicht unterstützt. Vor dem Aktivieren der CLR-Integration müssen Sie Lightweightpooling deaktivieren. Weitere Informationen finden Sie unter [Lightweightpooling (Serverkonfigurationsoption)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Siehe auch  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CLR-fähig (Serverkonfigurationsoption)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [Rollen auf Serverebene](../security/authentication-access/server-level-roles.md)  
  
  
