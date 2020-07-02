---
title: sp_catalogs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_catalogs_TSQL
- sp_catalogs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_catalogs
ms.assetid: ebb29ee2-be65-4e09-9c53-e3c6d12633e1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 155653adbfdb7902eb30e82dbade7fa3589ae00f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715967"
---
# <a name="sp_catalogs-transact-sql"></a>sp_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Liste von Katalogen des angegebenen Verbindungsservers zurück. Dies entspricht Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_catalogs [ @server_name = ] 'linked_svr'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server_name = ] 'linked_svr'`Der Name eines Verbindungs Servers. *linked_svr* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Catalog_name**|**nvarchar (** 128 **)**|Name des Katalogs|  
|**Beschreibung**|**nvarchar (** 4000 **)**|Eine Beschreibung des Katalogs.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Kataloginformationen für den Verbindungsserver `OLE DB ODBC Linked Server #3` zurückgegeben.  
  
> [!NOTE]  
>  Damit **sp_catalogs** nützliche Informationen bereitstellen können, `OLE DB ODBC Linked Server #3` muss bereits vorhanden sein.  
  
```  
USE master;  
GO  
EXEC sp_catalogs 'OLE DB ODBC Linked Server #3';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addlinkedserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_columns_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
