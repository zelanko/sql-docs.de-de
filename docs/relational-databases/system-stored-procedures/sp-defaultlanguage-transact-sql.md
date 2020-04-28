---
title: sp_defaultlanguage (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_defaultlanguage
- sp_defaultlanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultlanguage
ms.assetid: 908d01cc-e704-45d9-9e85-d2df6da3e6f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: af2402ce4f1e49ee572a9d271497c2798d679070
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68120089"
---
# <a name="sp_defaultlanguage-transact-sql"></a>sp_defaultlanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Standardsprache für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Alter Login](../../t-sql/statements/alter-login-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_defaultlanguage [ @loginame = ] 'login'   
     [ , [ @language = ] 'language' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'`Der Anmelde Name. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. der *Anmelde* Name kann eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhandene Anmeldung oder ein Windows-Benutzer oder eine Windows-Gruppe sein.  
  
`[ @language = ] 'language'`Die Standardsprache des Anmelde namens. *language* ist vom Datentyp **sysname**und hat den Standardwert NULL. die *Sprache* muss eine gültige Sprache auf dem Server sein. Wenn *Language* nicht angegeben wird, wird *Sprache* auf die Standardsprache des Servers festgelegt. die Standardsprache wird durch die **Standardsprache**der **sp_configure** Konfigurationsvariablen definiert. Wird die Standardsprache des Servers geändert, ändert sich dadurch nicht die Standardsprache der vorhandenen Anmeldenamen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_defaultlanguage** ruft Alter Login auf, wodurch zusätzliche Optionen unterstützt werden. Weitere Informationen zum Ändern anderer Anmelde Einstellungen finden Sie unter [Alter Login &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md).  
  
 Mit der SET LANGUAGE-Anweisung können Sie die Sprache der aktuellen Sitzung ändern. Verwenden Sie die@LANGUAGE @-Funktion, um die aktuelle Spracheinstellung anzuzeigen.  
  
 Wenn die Standardsprache eines Anmeldenamens vom Server gelöscht wird, übernimmt der Anmeldename die Standardsprache des Servers. **sp_defaultlanguage** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
 Informationen zu den auf dem Server installierten Sprachen sind in der **sys. syslanguages** -Katalog Sicht sichtbar.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `ALTER LOGIN` zum Ändern der Standardsprache für den Anmeldenamen `Fathima` auf Arabisch geändert. Dies ist die bevorzugte Methode.  
  
```  
ALTER LOGIN Fathima WITH DEFAULT_LANGUAGE = Arabic;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Alter Login &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET-Anweisungen (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [sys. syslanguages &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
