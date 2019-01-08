---
title: Sp_deletemergeconflictrow (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords:
- sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1b11096a9f1ac9f8c5f5c04f3afc36f2776e988e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52782952"
---
# <a name="spdeletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht Zeilen aus einer Konflikttabelle oder [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) Tabelle. Diese gespeicherte Prozedur wird für jede Datenbank auf dem Computer ausgeführt, auf dem die Konflikttabelle gespeichert ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@conflict_table=**] **"**_Conflict_table_**"**  
 Der Name der Konflikttabelle. *Conflict_table* ist **Sysname**, hat den Standardwert **%**. Wenn die *Conflict_table* als NULL angegeben wird oder **%**, des Konflikts wird davon ausgegangen, dass ein Delete-Konflikt und die übereinstimmt *Rowguid* und *Origin_datasource* und *Source_object* gelöscht wird, aus der [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) Tabelle.  
  
 [  **@source_object=**] **"**_Source_object_**"**  
 Der Name der Quelltabelle. *Source_object* ist **nvarchar(386)**, hat den Standardwert NULL.  
  
 [  **@rowguid =**] **"**_Rowguid_**"**  
 Die Zeilen-ID für den Löschkonflikt. *ROWGUID* ist **Uniqueidentifier**, hat keinen Standardwert.  
  
 [  **@origin_datasource=**] **"**_Origin_datasource_**"**  
 Der Ursprung des Konflikts. *Origin_datasource* ist **varchar(255)**, hat keinen Standardwert.  
  
 [  **@drop_table_if_empty=**] **"**_Drop_table_if_empty_**"**  
 Ein Flag gibt an, dass die *Conflict_table* soll, wenn gelöscht werden, ist leer. *Drop_table_if_empty* ist **varchar(10)**, hat den Standardwert "false".  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_deletemergeconflictrow** wird bei der Mergereplikation verwendet.  
  
 [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) Tabelle eine Systemtabelle und wird nicht aus der Datenbank gelöscht, selbst wenn es leer ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_deletemergeconflictrow**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
