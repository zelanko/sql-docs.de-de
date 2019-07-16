---
title: Abfragen von erweiterten gespeicherten Prozeduren, die in SQLServer installierten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.openlocfilehash: 33c2e4d945f4db077df843bd5622d883c719fd85
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064323"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Abfragen von in SQL Server installierten erweiterten gespeicherten Prozeduren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentifizierter Benutzer kann anzeigen, die zurzeit definierten erweiterten gespeicherten Prozeduren und der Namen der DLL für jedes gehört, indem Sie Ausführung der **Sp_helpextendedproc** Systemprozedur. Das folgende Beispiel gibt beispielsweise die DLL zurück, zu dem **Xp_hello** gehört:  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Wenn **Sp_helpextendedproc** wird ausgeführt, ohne Angabe einer erweiterten gespeicherten Prozedur, die alle erweiterten gespeicherten Prozeduren und ihre DLLs angezeigt werden.  
  
> [!IMPORTANT]  
>  Informationen werden nur für die erweiterten gespeicherten Prozeduren zurückgegeben, deren Besitzer der Benutzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Nur Mitglieder der der **Sysadmin** Serverrolle und die **Db_owner**, **Db_securityadmin**, und die **Db_ddladmin** fester Datenbankname Rollen können Informationen zu allen erweiterten gespeicherten Prozeduren anzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
