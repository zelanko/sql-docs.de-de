---
title: Sp_help_category (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 05e5ef298e9365b63b4e66b93c0f2aa637be8312
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706998"
---
# <a name="sphelpcategory-transact-sql"></a>sp_help_category (Transact-SQL)
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
 [ **@class=**] **'***class***'**  
 Die Klasse, zu der Informationen angefordert werden. *Klasse* ist **varchar(8)**, hat den Standardwert des **Auftrag**. *Klasse* kann einen der folgenden Werte sein.  
  
|value|Description|  
|-----------|-----------------|  
|**JOB**|Stellt Informationen zu einer Auftragskategorie bereit.|  
|**WARNUNG**|Stellt Informationen zu einer Warnungskategorie bereit.|  
|**OPERATOR**|Stellt Informationen zu einer Operatorkategorie bereit.|  
  
 [ **@type=** ] **'***type***'**  
 Der Typ der Kategorie, für die Informationen angefordert werden. *Typ* ist **varchar(12)**, hat den Standardwert NULL und kann einen der folgenden Werte sein.  
  
|value|Description|  
|-----------|-----------------|  
|**LOCAL**|Lokale Auftragskategorie|  
|**MULTI-SERVER**|Multiserver-Auftragskategorie|  
|**NONE**|Kategorie für eine andere Klasse als **Auftrag**.|  
  
 [ **@name=** ] **'***name***'**  
 Der Name der Kategorie, für die Informationen angefordert werden. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
 [ **@suffix=** ] *suffix*  
 Gibt an, ob die **Category_type** Spalte im Resultset ist eine ID oder einen Namen. *Suffix* ist **Bit**, hat den Standardwert **0**. **1** zeigt die **Category_type** als einen Namen ein, und **0** deckt das Diagramm als ID  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn **@suffix** ist **0**, **Sp_help_category** gibt das folgende Resultset zurück:  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|Kategorie-ID|  
|**category_type**|**tinyint**|Der Typ der Kategorie:<br /><br /> **1** = lokal<br /><br /> **2** = Multiserver<br /><br /> **3** = keine|  
|**name**|**sysname**|Kategoriename|  
  
 Wenn **@suffix** ist **1**, **Sp_help_category** gibt das folgende Resultset zurück:  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|Kategorie-ID|  
|**category_type**|**sysname**|Art der Kategorie: Einer der **lokalen**, **mit mehreren Servern**, oder **NONE**|  
|**name**|**sysname**|Kategoriename|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_help_category** muss ausgeführt werden, aus der **Msdb** Datenbank.  
  
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
  
  
