---
title: Sp_procoption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_procoption
- sp_procoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_procoption
ms.assetid: 6f0221bd-70b4-4b04-b15d-722235aceb3c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 218371ab6d8133dbaf1865eeffc11f92883b4305
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533672"
---
# <a name="spprocoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt die automatische Ausführung einer gespeicherten Prozedur fest oder löscht diese. Eine gespeicherte Prozedur, die auf automatische Ausführung führt jedes Mal eine Instanz der festgelegt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestartet wird.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @ProcName = ] 'procedure'` Ist der Name der Prozedur für die eine Option festgelegt. *Prozedur* ist **nvarchar(776)**, hat keinen Standardwert.  
  
`[ @OptionName = ] 'option'` Ist der Name der festzulegenden Option. Der einzige Wert für *Option* ist **Start**.  
  
`[ @OptionValue = ] 'value'` Gibt an, ob die Option auf (**"true"** oder **auf**) oder off (**"false"** oder **aus**). *Wert* ist **varchar(12)**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Fehlernummer (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Startprozeduren müssen werden die **master** Datenbank und darf keine Eingabe-oder Ausgabe enthalten. Die Ausführung der gespeicherten Prozeduren beginnt, wenn alle Datenbanken wiederhergestellt sind und beim Start die Meldung "Die Wiederherstellung ist abgeschlossen" protokolliert wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird für eine Prozedur die automatische Ausführung festgelegt.  
  
```  
EXEC sp_procoption @ProcName = N'<procedure name>'   
    , @OptionName = 'startup'   
    , @OptionValue = 'on';   
```  
  
 Im folgenden Beispiel wird die automatische Ausführung einer Prozedur verhindert.  
  
```  
EXEC sp_procoption @ProcName = N'<procedure name>'      
    , @OptionName = 'startup'
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen einer gespeicherten Prozedur](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
