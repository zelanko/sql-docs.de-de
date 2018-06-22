---
title: Entladen eine erweiterte gespeicherte Prozedur DLL | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 78d3e74d7316b31143253a2c1bd7c33d08b012f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148833"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Entfernen der DLL einer erweiterten gespeicherten Prozedur aus dem Arbeitsspeicher
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Lädt die DLL eine erweiterte gespeicherte Prozedur an, wie die Funktionen der DLL aufgerufen wird. Die DLL bleibt so lange im Arbeitsspeicher, bis der Server heruntergefahren wird oder der Systemadministrator die DLL mit der DBCC-Anweisung aus dem Arbeitsspeicher entfernt. Mit diesem Befehl z. B. entlädt die **xp_hello.dll**, sodass der Systemadministrator eine neuere Version dieser Datei in das Verzeichnis kopieren, ohne den Server herunterzufahren:  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DBCC-DLL-Namen &#40;frei&#41; &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
