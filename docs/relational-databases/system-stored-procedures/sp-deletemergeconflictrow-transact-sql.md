---
title: sp_deletemergeconflictrow (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5d778a90adf2579ca136603847762b2577a5155f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830278"
---
# <a name="sp_deletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht Zeilen aus einer Konflikt Tabelle oder der [MSmerge_conflicts_info &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) Tabelle. Diese gespeicherte Prozedur wird für jede Datenbank auf dem Computer ausgeführt, auf dem die Konflikttabelle gespeichert ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @conflict_table = ] 'conflict_table'`Der Name der Konflikt Tabelle. *conflict_table* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **%** . Wenn die *conflict_table* als NULL oder angegeben wird **%** , wird davon ausgegangen, dass es sich um einen Lösch Konflikt handelt und die Zeilen übereinstimmende *ROWGUID* und *origin_datasource* und *source_object* aus der [MSmerge_conflicts_info &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) Tabelle gelöscht werden.  
  
`[ @source_object = ] 'source_object'`Der Name der Quell Tabelle. *source_object* ist vom Datentyp **nvarchar (386)** und hat den Standardwert NULL.  
  
`[ @rowguid = ] 'rowguid'`Der Zeilen Bezeichner für den Lösch Konflikt. *ROWGUID* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert.  
  
`[ @origin_datasource = ] 'origin_datasource'`Der Ursprung des Konflikts. *origin_datasource* ist vom Datentyp **varchar (255)** und hat keinen Standardwert.  
  
`[ @drop_table_if_empty = ] 'drop_table_if_empty'`Ein Flag, das angibt, dass die *conflict_table* gelöscht werden soll, wenn leer ist. *drop_table_if_empty* ist vom Datentyp **varchar (10)** und hat den Standardwert false.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_deletemergeconflictrow** wird bei der Mergereplikation verwendet.  
  
 [MSmerge_conflicts_info &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) Tabelle ist eine Systemtabelle und wird nicht aus der Datenbank gelöscht, auch wenn Sie leer ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_deletemergeconflictrow**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
