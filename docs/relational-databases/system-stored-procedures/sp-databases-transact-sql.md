---
title: Sp_databases (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_databases_TSQL
- sp_databases
dev_langs:
- TSQL
helpviewer_keywords:
- sp_databases
ms.assetid: 2a83b92a-9ecc-43c4-8ff4-e91e3a940b5a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1be4fbfb6ce30443a979fb500954e7aa8fa9779a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614923"
---
# <a name="spdatabases-transact-sql"></a>sp_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet die Datenbanken, die entweder in einer Instanz von befinden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder über ein Datenbankgateway zugegriffen werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_databases  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 None  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**DATABASE_NAME**|**sysname**|Der Name der Datenbank. In der [!INCLUDE[ssDE](../../includes/ssde-md.md)], stellt diese Spalte den Datenbanknamen dar, gespeichert in der **sys.databases** -Katalogsicht angezeigt.|  
|**DATABASE_SIZE**|**int**|Die Größe der Datenbank in Kilobyte.|  
|**"HINWEISE"**|**varchar(254)**|Für die [!INCLUDE[ssDE](../../includes/ssde-md.md)], dieses Feld gibt immer NULL zurück.|  
  
## <a name="remarks"></a>Hinweise  
 Die zurückgegebenen Datenbanknamen können als Parameter für die USE-Anweisung verwendet werden, um den aktuellen Datenbankkontext zu ändern.  
  
 Für**sp_databases** gibt es in Open Database Connectivity (ODBC) keine Entsprechung.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Berechtigung CREATE DATABASE oder ALTER ANY DATABASE oder VIEW ANY DEFINITION sowie die Zugriffsberechtigung für die Datenbank. Die VIEW ANY DEFINITION-Berechtigung darf nicht verweigert worden sein.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Ausführung von `sp_databases`.  
  
```sql  
USE master;  
GO  
EXEC sp_databases;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [HAS_DBACCESS &#40;Transact-SQL&#41;](../../t-sql/functions/has-dbaccess-transact-sql.md)  
  
  
