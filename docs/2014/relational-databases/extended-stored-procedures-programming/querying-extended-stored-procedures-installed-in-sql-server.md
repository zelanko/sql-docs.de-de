---
title: Abfragen von erweiterten gespeicherten Prozeduren, die in SQLServer installierten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9f62c0dea02ee4c6f9bccda0dfaf7e7932c1dab7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62511933"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Abfragen von in SQL Server installierten erweiterten gespeicherten Prozeduren
    
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
 [sp_helpextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql)   
 [sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
