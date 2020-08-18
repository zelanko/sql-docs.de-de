---
description: Entfernen der DLL einer erweiterten gespeicherten Prozedur aus dem Arbeitsspeicher
title: Entladen einer DLL für eine erweiterte gespeicherte Prozedur | Microsoft-Dokumentation
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
ms.openlocfilehash: f409b15fe8212ca3d5ce25334a0241eb38feea9b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88408786"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Entfernen der DLL einer erweiterten gespeicherten Prozedur aus dem Arbeitsspeicher
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]lädt eine DLL für eine erweiterte gespeicherte Prozedur, sobald ein-Vorgang an eine der Funktionen der dll erfolgt. Die DLL bleibt so lange im Arbeitsspeicher, bis der Server heruntergefahren wird oder der Systemadministrator die DLL mit der DBCC-Anweisung aus dem Arbeitsspeicher entfernt. Dieser Befehl entlädt z. b. die **xp_hello.dll**und ermöglicht dem Systemadministrator, eine neuere Version dieser Datei in das Verzeichnis zu kopieren, ohne den Server herunterzufahren:  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DBCC dllname &#40;frei&#41; &#40;Transact-SQL-&#41;](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)  
  
  
