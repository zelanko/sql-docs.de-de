---
title: Sp_dbfixedrolepermission (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbfixedrolepermission
- sp_dbfixedrolepermission_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbfixedrolepermission
ms.assetid: b8c30191-f532-49cd-83f3-c271f63ce572
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91a7278230a0e7201e78354a38af58f417ac26ce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108163"
---
# <a name="spdbfixedrolepermission-transact-sql"></a>sp_dbfixedrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt die Berechtigungen einer festen Datenbankrolle an. **Sp_dbfixedrolepermission** gibt korrekte Informationen in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Die Ausgabe spiegelt nicht die Änderungen an der Berechtigungshierarchie, die in implementiert wurden [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Weitere Informationen finden Sie unter[Berechtigungen &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-database-engine.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dbfixedrolepermission [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'` Der Name einer gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] festen Datenbankrolle. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn *Rolle* nicht angegeben ist, werden die Berechtigungen für alle festen Datenbankrollen angezeigt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|Name der festen Datenbankrolle|  
|**Berechtigung**|**nvarchar(70)**|Zugeordneten Berechtigungen **DbFixedRole**|  
  
## <a name="remarks"></a>Hinweise  
 Führen Sie zum Anzeigen einer Liste der festen Datenbankrollen **Sp_helpdbfixedrole**. In der folgenden Tabelle werden die festen Datenbankrollen angezeigt.  
  
|Feste Datenbankrolle|Beschreibung|  
|-------------------------|-----------------|  
|**db_owner**|Datenbankbesitzer|  
|**db_accessadmin**|Administratoren für den Datenbankzugriff|  
|**db_securityadmin**|Administratoren für die Datenbanksicherheit|  
|**db_ddladmin**|DDL-Administratoren (Data Definition Language, Datendefinitionssprache) für die Datenbank|  
|**db_backupoperator**|Datenbanksicherungs-Operatoren|  
|**db_datareader**|Datenbank-Datenleser|  
|**db_datawriter**|Datenbank-Datenschreiber|  
|**db_denydatareader**|Datenbank-Verweigerungsdatenleser|  
|**db_denydatawriter**|Datenbank-Verweigerungsdatenschreiber|  
  
 Mitglieder der **Db_owner** festen Datenbankrolle haben die Berechtigungen aller anderen festen Datenbankrollen. Führen Sie zum Anzeigen der Berechtigungen für den festen Serverrollen **Sp_srvrolepermission**.  
  
 Das Resultset enthält die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen, die ausgeführt werden können, sowie andere spezielle Aktivitäten, die von Mitgliedern der Datenbankrolle ausgeführt werden können.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage gibt die Berechtigungen für alle festen Datenbankrollen zurück, weil keine feste Datenbankrolle angegeben ist.  
  
```  
EXEC sp_dbfixedrolepermission;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [Sp_helpdbfixedrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md)   
 [sp_srvrolepermission &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
