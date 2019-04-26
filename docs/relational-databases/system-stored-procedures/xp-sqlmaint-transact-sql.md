---
title: Xp_sqlmaint (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_sqlmaint
- xp_sqlmaint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sqlmaint
ms.assetid: bda66e1b-6bbd-49be-b86e-37efc920e912
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2157462ca1f9509034f33208cce7aed2983ae4f2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62644791"
---
# <a name="xpsqlmaint-transact-sql"></a>xp_sqlmaint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ruft die **Sqlmaint** -Hilfsprogramm mit der eine Zeichenfolge mit **Sqlmaint**Switches. Die **Sqlmaint** -Hilfsprogramm führt eine Reihe von Wartungsvorgänge für eine oder mehrere Datenbanken.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_sqlmaint 'switch_string'     
```  
  
## <a name="arguments"></a>Argumente  
 **'** *switch_string* **'**  
 Eine Zeichenfolge, enthält die **Sqlmaint** Optionen des Hilfsprogramms. Die Optionen und ihre Werte müssen durch ein Leerzeichen getrennt werden.  
  
 Die **-?** Switch ist nicht gültig für **Xp_sqlmaint**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine. Gibt einen Fehler zurück, wenn die **Sqlmaint** Dienstprogramm ein Fehler auftritt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Prozedur von einem Benutzer, die mit SQL Server-Authentifizierung angemeldet aufgerufen, wird der **- U "***Login_id***"** und **-P "***Kennwort***"** Switches werden *Switch_string* vor der Ausführung. Wenn der Benutzer mit Windows-Authentifizierung angemeldet ist *Switch_string* übergeben wird, ohne Änderung **Sqlmaint**.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel ruft `xp_sqlmaint` das Hilfsprogramm `sqlmaint` auf, um Integritätsprüfungen auszuführen, eine Berichtsdatei zu erstellen und `msdb.dbo.sysdbmaintplan_history` zu aktualisieren.  
  
```  
EXEC xp_sqlmaint '-D AdventureWorks2012 -PlanID 02A52657-D546-11D1-9D8A-00A0C9054212   
   -Rpt "C:\Program Files\Microsoft SQL Server\MSSQL\LOG\DBMaintPlan2.txt" -WriteHistory  -CkDB -CkAl';   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The command(s) executed successfully.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sqlmaint (Hilfsprogramm)](../../tools/sqlmaint-utility.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
