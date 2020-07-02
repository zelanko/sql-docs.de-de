---
title: Abfragen von erweiterten gespeicherten Prozeduren
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
ms.custom: seo-dt-2019
ms.openlocfilehash: 8413f071cfb36f5cad9130d3e2b56327d9b3bf45
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758094"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Abfragen von in SQL Server installierten erweiterten gespeicherten Prozeduren
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentifizierter Benutzer kann die zurzeit definierten erweiterten gespeicherten Prozeduren und den Namen der dll, zu der jeder gehört, anzeigen, indem er die **sp_helpextendedproc** System Prozedur ausführen. Im folgenden Beispiel wird z. b. die dll zurückgegeben, zu der **xp_hello** gehört:  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Wenn **sp_helpextendedproc** ohne Angabe einer erweiterten gespeicherten Prozedur ausgeführt wird, werden alle erweiterten gespeicherten Prozeduren und ihre DLLs angezeigt.  
  
> [!IMPORTANT]  
>  Informationen werden nur für die erweiterten gespeicherten Prozeduren zurückgegeben, deren Besitzer der Benutzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Nur Mitglieder der festen Server Rolle **sysadmin** und der **db_owner**, **db_securityadmin**und der festen Daten Bank Rolle **db_ddladmin** können Informationen zu allen erweiterten gespeicherten Prozeduren anzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_helpextendedproc &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
