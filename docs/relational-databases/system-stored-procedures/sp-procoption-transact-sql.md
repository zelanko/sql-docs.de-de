---
title: sp_procoption (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: bc004c611c218324ce2d2d8b764b3ab05cb73e5d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67896593"
---
# <a name="sp_procoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt die automatische Ausführung einer gespeicherten Prozedur fest oder löscht diese. Eine gespeicherte Prozedur, die auf die automatische Ausführung festgelegt ist, wird jedes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Mal ausgeführt, wenn eine Instanz von gestartet wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @ProcName = ] 'procedure'`Der Name der Prozedur, für die eine Option festgelegt werden soll. die *Prozedur* ist vom Datentyp **nvarchar (776)** und hat keinen Standardwert.  
  
`[ @OptionName = ] 'option'`Der Name der festzulegenden Option. Der einzige Wert für *Option* ist " **Start**".  
  
`[ @OptionValue = ] 'value'`Gibt an, ob die Option aktiviert (**true** oder **on**) oder Off (**false** oder **Off**) festgelegt werden soll. der Wert ist vom Datentyp **varchar (12)** und hat keinen Standard *Wert* .  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Fehlernummer (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Start Prozeduren müssen in der **Master** -Datenbank enthalten sein und dürfen keine Eingabe-oder Ausgabeparameter enthalten. Die Ausführung der gespeicherten Prozeduren beginnt, wenn alle Datenbanken wiederhergestellt sind und beim Start die Meldung "Die Wiederherstellung ist abgeschlossen" protokolliert wird.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen einer gespeicherten Prozedur](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
