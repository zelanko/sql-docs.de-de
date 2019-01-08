---
title: Entfernen einer erweiterten gespeicherten Prozedur aus SQLServer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bcb58ac180861641803147d1dfea621bd52df9a6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804022"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Entfernen einer erweiterten gespeicherten Prozedur aus SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 So löschen Sie jede Funktion der erweiterten gespeicherten Prozedur in einer benutzerdefinierten erweiterten gespeicherten Prozedur-DLL einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss vom Systemadministrator ausgeführt der **Sp_dropextendedproc** gespeicherte Systemprozedur, die den Namen eines der Funktion und den Namen der DLL an, in dem sich die Funktion befindet. Angenommen, dieser Befehl entfernt die Funktion **Xp_hello**befindet sich in einer DLL, die mit dem Namen xp_hello.dll befindet, vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 Beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **Sp_dropextendedproc** erweiterte gespeicherte Systemprozeduren nicht gelöscht. Stattdessen sollte der Systemadministrator EXECUTE-Berechtigung für die erweiterte gespeicherte Prozedur zum Verweigern der **öffentliche** Rolle.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
