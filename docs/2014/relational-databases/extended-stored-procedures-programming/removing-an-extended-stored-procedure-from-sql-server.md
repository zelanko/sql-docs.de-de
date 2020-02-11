---
title: Entfernen einer erweiterten gespeicherten Prozedur aus SQL Server | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62512025"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Entfernen einer erweiterten gespeicherten Prozedur aus SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Verwenden Sie stattdessen die CLR-Integration.  
  
 Um jede Funktion der erweiterten gespeicherten Prozedur in einer benutzerdefinierten DLL einer benutzerdefinierten erweiterten gespeicherten Prozedur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu löschen, muss ein Systemadministrator die gespeicherte Prozedur des **sp_dropextendedproc** -Systems ausführen und dabei den Namen der Funktion und den Namen der DLL angeben, in der sich die Funktion befindet. Beispielsweise entfernt dieser Befehl die Funktion **xp_hello**, die sich in einer DLL mit dem Namen xp_hello. dll [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]befindet, aus:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]Ab **sp_dropextendedproc** keine erweiterten gespeicherten Prozeduren für das System ablegen. Stattdessen sollte der Systemadministrator die EXECUTE-Berechtigung für die erweiterte gespeicherte Prozedur der **Public** -Rolle verweigern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
