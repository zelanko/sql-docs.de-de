---
title: Entfernen einer erweiterten gespeicherten Prozedur-DLL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
ms.openlocfilehash: 159be22fcaba28183c8b6cc5089906c19bf2b765
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064258"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Entfernen der DLL einer erweiterten gespeicherten Prozedur aus dem Arbeitsspeicher
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Lädt die DLL eine erweiterte gespeicherte Prozedur an, sobald eine der Funktionen der DLL aufgerufen wird. Die DLL bleibt so lange im Arbeitsspeicher, bis der Server heruntergefahren wird oder der Systemadministrator die DLL mit der DBCC-Anweisung aus dem Arbeitsspeicher entfernt. Beispielsweise folgenden Befehl wird die **xp_hello.dll**, sodass der Systemadministrator eine neuere Version dieser Datei in das Verzeichnis kopieren, ohne den Server herunterzufahren:  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DBCC Dllname &#40;FREE&#41; &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)  
  
  
