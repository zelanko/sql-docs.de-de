---
title: sp_bindsession (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9a079a279c9d342033086c565203f85ad360e753
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828493"
---
# <a name="sp_bindsession-transact-sql"></a>sp_bindsession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Bindet eine Sitzung an andere Sitzungen in derselben Instanz von oder hebt Sie auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Bei Sitzungsbindungen können zwei oder mehr Sitzungen an derselben Transaktion teilnehmen und freigegebene Sperren verwenden, bis eine ROLLBACK TRANSACTION- oder COMMIT TRANSACTION-Anweisung ausgegeben wird.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen Multiple Active Results Sets (MARS) oder verteilte Transaktionen. Weitere Informationen finden Sie unter [Verwenden von Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_bindsession { 'bind_token' | NULL }  
```  
  
## <a name="arguments"></a>Argumente  
 **"** *bind_token* **"**  
 Das Token, das die Transaktion identifiziert, die ursprünglich mithilfe von **sp_getbindtoken** oder der Open Data Services **srv_getbindtoken** -Funktion abgerufen wurde. *bind_token*ist vom Datentyp **varchar (255)**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Zwei gebundene Sitzungen verwenden nur eine Transaktion und Sperren gemeinsam. Jede Sitzung behält ihre eigene Isolationsstufe. Das Festlegen einer neuen Isolationsstufe für eine Sitzung hat keine Auswirkungen auf die Isolationsstufe der anderen Sitzung. Jede Sitzung wird weiterhin über ihr Sicherheitskonto identifiziert und kann nur auf die Datenbankressourcen zugreifen, für die dem Konto Berechtigungen erteilt wurden.  
  
 **sp_bindsession** ein Bindungs Token verwendet, um zwei oder mehr vorhandene Client Sitzungen zu binden. Diese Clientsitzungen müssen zu derselben Instanz vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] gehören, von der der Bindungstoken erhalten wurde. Eine Sitzung ist ein Client, der einen Befehl ausführt. Gebundene Datenbanksitzungen verwenden einen Transaktions- und Sperrbereich gemeinsam.  
  
 Ein von einer Instanz vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgegebenes Bindungstoken kann nicht für eine Clientsitzung mit einer anderen Instanz verwendet werden, auch nicht bei DTC-Transaktionen. Ein Bindungstoken ist nur lokal innerhalb einer Instanz gültig und kann nicht auf mehreren Instanzen freigegeben werden. Zum Binden von Client Sitzungen auf eine andere Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] müssen Sie ein anderes Bindungs Token abrufen, indem Sie **sp_getbindtoken**ausführen.  
  
 **sp_bindsession** schlägt mit einem Fehler fehl, wenn ein Token verwendet wird, das nicht aktiv ist.  
  
 Aufheben der Bindung an eine Sitzung entweder mithilfe **sp_bindsession** , ohne *bind_token* anzugeben, oder durch Übergeben von NULL in *bind_token*.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das angegebene Bindungstoken an die aktuelle Sitzung gebunden.  
  
> [!NOTE]  
>  Das Bindungs Token, das im Beispiel angezeigt wird, wurde durch Ausführen von **sp_getbindtoken** vor dem Ausführen **sp_bindsession**abgerufen.  
  
```  
USE master;  
GO  
EXEC sp_bindsession 'BP9---5---->KB?-V'<>1E:H-7U-]ANZ';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_getbindtoken &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [srv_getbindtoken &#40;API für erweiterte gespeicherte Prozeduren&#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
