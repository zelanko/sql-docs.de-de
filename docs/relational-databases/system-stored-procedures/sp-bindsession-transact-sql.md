---
title: Sp_bindsession (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindsession
- sp_bindsession_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindsession
ms.assetid: 1436fe21-ad00-4a98-aca1-1451a5e571d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a24c219937341b7c1f9d44515bf52c4de220d4c2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996604"
---
# <a name="spbindsession-transact-sql"></a>sp_bindsession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Bindet eine Sitzung oder hebt die Bindung einer Sitzungs mit anderen Sitzungen in der gleichen Instanz von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Bei Sitzungsbindungen können zwei oder mehr Sitzungen an derselben Transaktion teilnehmen und freigegebene Sperren verwenden, bis eine ROLLBACK TRANSACTION- oder COMMIT TRANSACTION-Anweisung ausgegeben wird.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen Multiple Active Results Sets (MARS) oder verteilte Transaktionen. Weitere Informationen finden Sie unter [Verwenden von Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_bindsession { 'bind_token' | NULL }  
```  
  
## <a name="arguments"></a>Argumente  
 **'** *bind_token* **'**  
 Wird das Token, die Transaktion identifiziert, ursprünglich mit abgerufen **Sp_getbindtoken** oder der Open Data Services **Srv_getbindtoken** Funktion. *bind_token*is **varchar(255)**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Zwei gebundene Sitzungen verwenden nur eine Transaktion und Sperren gemeinsam. Jede Sitzung behält ihre eigene Isolationsstufe. Das Festlegen einer neuen Isolationsstufe für eine Sitzung hat keine Auswirkungen auf die Isolationsstufe der anderen Sitzung. Jede Sitzung wird weiterhin über ihr Sicherheitskonto identifiziert und kann nur auf die Datenbankressourcen zugreifen, für die dem Konto Berechtigungen erteilt wurden.  
  
 **Sp_bindsession** mithilfe eines Bindungstokens um zwei oder mehr vorhandene Clientsitzungen zu binden. Diese Clientsitzungen müssen zu derselben Instanz vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] gehören, von der der Bindungstoken erhalten wurde. Eine Sitzung ist ein Client, der einen Befehl ausführt. Gebundene Datenbanksitzungen verwenden einen Transaktions- und Sperrbereich gemeinsam.  
  
 Ein von einer Instanz vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgegebenes Bindungstoken kann nicht für eine Clientsitzung mit einer anderen Instanz verwendet werden, auch nicht bei DTC-Transaktionen. Ein Bindungstoken ist nur lokal innerhalb einer Instanz gültig und kann nicht auf mehreren Instanzen freigegeben werden. Um Clientsitzungen auf einer anderen Instanz binden die [!INCLUDE[ssDE](../../includes/ssde-md.md)], Sie müssen ein anderes Bindungstoken abrufen, indem Sie Ausführung **Sp_getbindtoken**.  
  
 **Sp_bindsession** fehl mit Fehler, wenn es sich um ein Token verwendet, die nicht aktiv ist.  
  
 Aufheben der Bindung einer Sitzung, die entweder mit **Sp_bindsession** ohne *Bind_token* oder durch Übergabe von NULL-Wert in *Bind_token*.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das angegebene Bindungstoken an die aktuelle Sitzung gebunden.  
  
> [!NOTE]  
>  Durch Ausführen des Bindungstokens, das im Beispiel gezeigte abgerufen wurde **Sp_getbindtoken** vor der Ausführung **Sp_bindsession**.  
  
```  
USE master;  
GO  
EXEC sp_bindsession 'BP9---5---->KB?-V'<>1E:H-7U-]ANZ';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_getbindtoken &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [Srv_getbindtoken &#40;gespeicherte API für erweiterte Prozeduren&#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
