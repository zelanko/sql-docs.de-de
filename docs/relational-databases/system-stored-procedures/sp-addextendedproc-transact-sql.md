---
description: sp_addextendedproc (Transact-SQL)
title: sp_addextendedproc (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a64b9b173b6b76429723c47bcf55fab4257b073c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447404"
---
# <a name="sp_addextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Registriert den Namen einer neuen erweiterten gespeicherten Prozedur in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen die [CLR-Integration](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @functname = ] 'procedure'` Der Name der Funktion, die in der dll (Dynamic Link Library) aufgerufen werden soll. die *Prozedur* ist vom Datentyp **nvarchar (517)** und hat keinen Standardwert. die *Prozedur* kann optional den Besitzer Namen in der Form *Owner. function*enthalten.  
  
`[ @dllname = ] 'dll'` Der Name der dll, die die Funktion enthält. *dll* ist vom Datentyp **varchar (255)** und hat keinen Standardwert. Es ist empfehlenswert, den vollständigen Pfad der DLL anzugeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Nachdem eine erweiterte gespeicherte Prozedur erstellt wurde, muss Sie mit sp_addextendedproc hinzugefügt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **sp_addextendedproc** Weitere Informationen finden Sie unter [Hinzufügen einer erweiterten gespeicherten Prozedur zu SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md).  
  
 Diese Prozedur kann nur in der **Master** -Datenbank ausgeführt werden. Wenn Sie eine erweiterte gespeicherte Prozedur aus einer anderen Datenbank als der **Master**-Datenbank ausführen möchten, qualifizieren Sie den Namen der erweiterten gespeicherten Prozedur mit **Master**.  
  
 **sp_addextendedproc** fügt der [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) -Katalog Sicht Einträge hinzu, wobei der Name der neuen erweiterten gespeicherten Prozedur mit registriert wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Außerdem wird ein Eintrag in der [sys. extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) -Katalog Sicht hinzugefügt.  
  
> [!IMPORTANT]  
>  Vorhandene DLLs, die nicht mit einem vollständigen Pfad registriert wurden, sind nach dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nicht mehr funktionsfähig. Um das Problem zu beheben, verwenden Sie **sp_dropextendedproc** , um die Registrierung der dll aufzuheben, und registrieren Sie Sie dann erneut mit **sp_addextendedproc**, wobei Sie den gesamten Pfad angeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_addextendedproc**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die erweiterte gespeicherte Prozedur **xp_hello** hinzugefügt.  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
