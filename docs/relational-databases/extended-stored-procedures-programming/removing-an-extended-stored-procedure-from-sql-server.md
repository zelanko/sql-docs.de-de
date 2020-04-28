---
title: Entfernen einer erweiterten gespeicherten Prozedur
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.custom: seo-dt-2019
ms.openlocfilehash: ec61cf630d606977689d3fb3763cce8bd8b705c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74095435"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Entfernen einer erweiterten gespeicherten Prozedur aus SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Um jede Funktion der erweiterten gespeicherten Prozedur in einer benutzerdefinierten DLL einer benutzerdefinierten erweiterten gespeicherten Prozedur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu löschen, muss ein Systemadministrator die gespeicherte Prozedur des **sp_dropextendedproc** -Systems ausführen und dabei den Namen der Funktion und den Namen der DLL angeben, in der sich die Funktion befindet. Beispielsweise entfernt dieser Befehl die Funktion **xp_hello**, die sich in einer DLL mit dem Namen xp_hello. dll [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]befindet, aus:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]Ab **sp_dropextendedproc** keine erweiterten gespeicherten Prozeduren für das System ablegen. Stattdessen sollte der Systemadministrator die EXECUTE-Berechtigung für die erweiterte gespeicherte Prozedur der **Public** -Rolle verweigern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
