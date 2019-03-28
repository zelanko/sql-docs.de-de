---
title: Sp_helplogins (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplogins_TSQL
- sp_helplogins
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplogins
ms.assetid: f9ad3767-5b9f-420d-8922-b637811404f7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3461d6f80bb1ac693cca78954e5165fb7f012436
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529742"
---
# <a name="sphelplogins-transact-sql"></a>sp_helplogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu Anmeldenamen und den zugeordneten Benutzern in jeder Datenbank bereit.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helplogins [ [ @LoginNamePattern = ] 'login' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @LoginNamePattern = ] 'login'` Ist ein Anmeldename. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL. *login* muss vorhanden sein, wenn angegeben. Falls *login* nicht angegeben wird, werden Informationen zu allen Anmeldenamen zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Der erste Bericht enthält Informationen zu allen angegebenen Anmeldenamen (siehe folgende Tabelle).  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Benutzername|  
|**SID**|**varbinary(85)**|Sicherheits-ID (SID) für den Anmeldenamen.|  
|**DefDBName**|**sysname**|Standarddatenbank, die **LoginName** beim Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet.|  
|**DefLangName**|**sysname**|Von **LoginName**verwendete Standardsprache.|  
|**Auser**|**char(5)**|Yes = **LoginName** ist ein Benutzername in einer Datenbank zugeordnet.<br /><br /> No = **LoginName** ist kein Benutzername zugeordnet.|  
|**ARemote**|**char(7)**|Yes = **LoginName** ist ein Remoteanmeldename zugeordnet.<br /><br /> No = **LoginName** ist kein Anmeldename zugeordnet.|  
  
 Der zweite Bericht enthält Informationen zu den Benutzern, die den jeweiligen Anmeldenamen zugeordnet sind, und zu den Rollenmitgliedschaften des Anmeldenamens, wie in der folgenden Tabelle dargestellt.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Benutzername|  
|**DBName**|**sysname**|Standarddatenbank, die **LoginName** beim Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet.|  
|**UserName**|**sysname**|Benutzerkonto, dem **LoginName** in **DBName**zugeordnet ist, und die Rollen, denen **LoginName** in **DBName**angehört.|  
|**UserOrAlias**|**char(8)**|MemberOf = **UserName** ist eine Rolle.<br /><br /> User = **UserName** ist ein Benutzerkonto.|  
  
## <a name="remarks"></a>Hinweise  
 Bestimmen Sie mithilfe von **sp_helplogins** die Benutzerkonten, die dem Anmeldenamen zugeordnet sind, bevor Sie Anmeldenamen entfernen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **securityadmin** .  
  
 **sp_helplogins** muss alle Datenbanken auf dem Server überprüfen, um alle Benutzerkonten zu identifizieren, die einem bestimmten Anmeldenamen zugeordnet sind. Deshalb muss für jede Datenbank auf dem Server mindestens eine der folgenden Bedingungen zutreffen:  
  
-   Der Benutzer, der **sp_helplogins** ausführt, verfügt über die Berechtigung für den Zugriff auf die Datenbank.  
  
-   Das Benutzerkonto **guest** ist in der Datenbank aktiviert.  
  
 Falls **sp_helplogins** nicht auf eine Datenbank zugreifen kann, gibt **sp_helplogins** so viele Informationen wie möglich zurück und zeigt die Fehlermeldung 15622 an.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zum Anmeldenamen `John`zurückgegeben.  
  
```  
EXEC sp_helplogins 'John';  
GO  
  
LoginName SID                        DefDBName DefLangName AUser ARemote   
--------- -------------------------- --------- ----------- ----- -------   
John      0x23B348613497D11190C100C  master    us_english  yes   no  
  
(1 row(s) affected)  
  
LoginName   DBName   UserName   UserOrAlias   
---------   ------   --------   -----------   
John        pubs     John       User          
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
