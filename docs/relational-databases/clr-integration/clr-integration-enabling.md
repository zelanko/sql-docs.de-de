---
title: Aktivieren der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/17/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 07066dc7ffbd48273ace55e0c9867661b2cbfe59
ms.sourcegitcommit: 445842da7c7d216b94a9576e382164c67f54e19a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "71680857"
---
# <a name="clr-integration---enabling"></a>CLR-Integration: Aktivierung
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Die Funktion zur CLR-Integration (Common Language Runtime) ist standardmäßig deaktiviert und muss aktiviert werden, um Objekte, die mittels CLR-Integration implementiert werden, verwenden zu können. Um die CLR-Integration zu aktivieren, verwenden Sie die Option **CLR-fähig** der gespeicherten Prozedur **sp_configure** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
```sql  
EXEC sp_configure 'clr enabled', 1;  
RECONFIGURE;  
GO  
```  
  
 Sie können die CLR-Integration deaktivieren, indem Sie die Option **CLR-fähig** auf 0 festlegen. Wenn Sie die CLR-Integration deaktivieren, beendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Ausführung aller benutzerdefinierten CLR-Routinen und entlädt alle Anwendungs Domänen. Funktionen, die auf der CLR basieren, wie z. b. der **hierarchyid** -Datentyp, die `FORMAT` Funktion, die Replikation und die Richtlinien basierte Verwaltung, sind von dieser Einstellung nicht betroffen und funktionieren weiterhin.
  
> [!NOTE]  
>  Um die CLR-Integration zu aktivieren, müssen Sie über die ALTER SETTINGS-Berechtigung auf Serverebene verfügen, die von Mitgliedern der festen Server Rollen **sysadmin** und **serveradmin** implizit aufbewahrt wird.  
  
> [!NOTE]  
>  Computer, die mit großen Mengen an Arbeitsspeicher und einer großen Anzahl von Prozessoren konfiguriert sind, können das SQL Server-Funktion zur CLR-Integration beim Serverstart möglicherweise nicht laden. Um dieses Problem zu beheben, starten Sie den Server mithilfe der Startoption **-gmemory_to_reserve**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienst, und geben Sie einen Wert für den Arbeitsspeicher an, der groß genug ist. Weitere Informationen finden Sie unter [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  CLR (Common Language Runtime) wird beim Lightweightpooling nicht unterstützt. Vor dem Aktivieren der CLR-Integration müssen Sie Lightweightpooling deaktivieren. Weitere Informationen finden Sie unter [Lightweightpooling (Serverkonfigurationsoption)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Siehe auch  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [CLR-fähig (Serverkonfigurationsoption)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
