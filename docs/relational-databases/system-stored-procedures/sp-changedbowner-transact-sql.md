---
description: sp_changedbowner (Transact-SQL)
title: sp_changedbowner (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dc4f29dba1a922b5adae32e0fc42cf714afc292f
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753483"
---
# <a name="sp_changedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert den Besitzer der aktuellen Datenbank.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @loginame =] '*Login*'  
 Die Anmelde-ID des neuen Besitzers der aktuellen Datenbank. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. die *Anmeldung* muss ein bereits vorhandener- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Name oder Windows-Benutzer sein. der *Anmelde* Name kann nicht zum Besitzer der aktuellen Datenbank werden, wenn er bereits über ein vorhandenes Benutzer Sicherheits Konto innerhalb der Datenbank auf die Datenbank zugreifen kann. Um dies zu vermeiden, löschen Sie zunächst den Benutzer innerhalb der aktuellen Datenbank.  
  
 [ @map =] *remap_alias_flag*  
 Der *remap_alias_flag* -Parameter ist veraltet, da die Anmeldungs Aliase aus entfernt wurden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die Verwendung des *remap_alias_flag* -Parameters führt nicht zu einem Fehler, hat jedoch keine Auswirkungen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Nach der Ausführung von sp_changedbowner ist der neue Besitzer als Benutzer dbo innerhalb der Datenbank bekannt. dbo besitzt die impliziten Berechtigungen, alle Aktivitäten in der Datenbank auszuführen.  
  
 Der Besitzer der Systemdatenbanken master, model oder tempdb kann nicht geändert werden.  
  
 Führen Sie die gespeicherte Prozedur sp_helplogins aus, um eine Liste der gültigen *Anmelde* Werte anzuzeigen.  
  
 Wenn Sie sp_changedbowner nur mit dem *Anmelde* Parameter ausführen, wird der Daten Bank Besitz in *Login*geändert.  
  
 Sie können den Besitzer jedes sicherungsfähigen Elements mit der ALTER AUTHORIZATION-Anweisung ändern. Weitere Informationen finden Sie unter [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die TAKE OWNERSHIP-Berechtigung für die Datenbank. Wenn der neue Besitzer über einen entsprechenden Benutzer in der Datenbank verfügt, wird die IMPERSONATE-Berechtigung für den Anmeldenamen benötigt. Andernfalls ist die CONTROL SERVER-Berechtigung auf dem Server erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Anmeldename `Albert` als Besitzer der aktuellen Datenbank festgelegt.  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md)   
 [sp_dropalias &#40;Transact-SQL-&#41;](./system-stored-procedures-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
