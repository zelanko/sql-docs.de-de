---
title: Abfragen von in SQL Server installierten erweiterten gespeicherten Prozeduren | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62511933"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Abfragen von in SQL Server installierten erweiterten gespeicherten Prozeduren
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentifizierter Benutzer kann die zurzeit definierten erweiterten gespeicherten Prozeduren und den Namen der dll, zu der jeder gehört, anzeigen, indem er die **sp_helpextendedproc** System Prozedur ausführen. Im folgenden Beispiel wird z. b. die dll zurückgegeben, zu der **xp_hello** gehört:  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Wenn **sp_helpextendedproc** ohne Angabe einer erweiterten gespeicherten Prozedur ausgeführt wird, werden alle erweiterten gespeicherten Prozeduren und ihre DLLs angezeigt.  
  
> [!IMPORTANT]  
>  Informationen werden nur für die erweiterten gespeicherten Prozeduren zurückgegeben, deren Besitzer der Benutzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Nur Mitglieder der festen Server Rolle **sysadmin** und der **db_owner**, **db_securityadmin**und der festen Daten Bank Rolle **db_ddladmin** können Informationen zu allen erweiterten gespeicherten Prozeduren anzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_helpextendedproc &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql)   
 [sp_addextendedproc &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
