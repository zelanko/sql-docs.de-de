---
title: sp_help_category (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_category
- sp_help_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_category
ms.assetid: 8cad1dcc-b43e-43bd-bea0-cb0055c84169
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1b44f5962e8241afa95b9e68cf75d493dff01ad5
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304803"
---
# <a name="sp_help_category-transact-sql"></a>sp_help_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu den angegebenen Klassen von Aufträgen, Warnungen oder Operatoren bereit.  
   
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_category [ [ @class = ] 'class' ]   
     [ , [ @type = ] 'type' ]   
     [ , [ @name = ] 'name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @class = ] 'class'` die Klasse, für die Informationen angefordert werden. die *Klasse* ist vom Datentyp **varchar (8)** und hat den Standardwert **Job**. die *Klasse* kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**JOB**|Stellt Informationen zu einer Auftragskategorie bereit.|  
|**WARNUNG**|Stellt Informationen zu einer Warnungskategorie bereit.|  
|**KOM**|Stellt Informationen zu einer Operatorkategorie bereit.|  
  
`[ @type = ] 'type'` der Typ der Kategorie, für die Informationen angefordert werden. *Type ist vom Datentyp* **varchar (12)** und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**LOCAL**|Lokale Auftrags Kategorie.|  
|**MULTISERVER**|Multiserver-Auftragskategorie|  
|**NONE**|Kategorie für eine andere Klasse als **Job**.|  
  
`[ @name = ] 'name'` der Name der Kategorie, für die Informationen angefordert werden. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
`[ @suffix = ] suffix` gibt an, ob die **category_type** -Spalte im Resultset eine ID oder ein Name ist. *Suffix* ist vom Typ **Bit**. der Standardwert ist **0**. **1** zeigt den **category_type** als Namen an, und **0** zeigt ihn als ID an.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn **\@suffix** **0**ist, gibt **sp_help_category** das folgende Resultset zurück:  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|Kategorie-ID|  
|**category_type**|**tinyint**|Typ der Kategorie:<br /><br /> **1** = lokal<br /><br /> **2** = MultiServer<br /><br /> **3** = keine|  
|**name**|**sysname**|Kategoriename|  
  
 Wenn **\@suffix** **1**ist, gibt **sp_help_category** das folgende Resultset zurück:  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|Kategorie-ID|  
|**category_type**|**sysname**|Art der Kategorie: Eine von " **local**", " **MultiServer**" oder " **None** ".|  
|**name**|**sysname**|Kategoriename|  
  
## <a name="remarks"></a>Hinweise  
 **sp_help_category** muss von der **msdb** -Datenbank aus ausgeführt werden.  
  
 Werden keine Parameter angegeben, stellt das Resultset Informationen zu allen Auftragskategorien bereit.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-local-job-information"></a>A. Zurückgeben von Informationen zu lokalen Aufträgen  
 Im folgenden Beispiel werden Informationen zu Aufträgen zurückgegeben, die lokal verwaltet werden.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @type = N'LOCAL' ;  
GO  
```  
  
### <a name="b-returning-alert-information"></a>B. Zurückgeben von Warnungsinformationen  
 Im folgenden Beispiel werden Informationen zur Warnungskategorie für die Replikation zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @class = N'ALERT',  
    @name = N'Replication' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
