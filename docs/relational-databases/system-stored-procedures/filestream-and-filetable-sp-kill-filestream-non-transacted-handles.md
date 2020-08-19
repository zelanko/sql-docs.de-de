---
description: sp_kill_filestream_non_transacted_handles (Transact-SQL)
title: sp_kill_filestream_non_transacted_handles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_kill_filestream_non_transacted_handles_TSQL
- sp_kill_filestream_non_transacted_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sp_kill_filestream_non_transacted_handles
ms.assetid: 7188353e-ab29-49a0-8f25-7fb8ab122589
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3413aa4b4601701241aeae9474d92964cd21238c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427702"
---
# <a name="sp_kill_filestream_non_transacted_handles-transact-sql"></a>sp_kill_filestream_non_transacted_handles (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Schließt nicht transaktionale Dateihandles für FileTable-Daten.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] 'table_name', [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>Argumente  
 *table_name*  
 Der Name der Tabelle, in der nicht transaktionale Handles zu schließen sind.  
  
 Sie können *table_name* ohne *handle_id* übergeben, um alle geöffneten nicht transaktionalen Handles für die FILETABLE zu schließen.  
  
 Sie können NULL für den Wert von *table_name* übergeben, um alle geöffneten nicht transaktionalen Handles für alle filetables in der aktuellen Datenbank zu schließen. Der Standardwert ist NULL.  
  
 *handle_id*  
 Die optionale ID des einzelnen Handles, der geschlossen werden soll. Sie können die *handle_id* aus der dynamischen Verwaltungs Sicht [sys. dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md) erhalten. Jede ID ist in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz eindeutig. Wenn Sie *handle_id*angeben, müssen Sie auch einen Wert für *table_name*angeben.  
  
 Sie können NULL für den Wert von *handle_id* übergeben, um alle geöffneten nicht transaktionalen Handles für die FILETABLE zu schließen, die von *table_name*angegeben wird. Der Standardwert ist NULL.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-set"></a>Resultset  
 Keine  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Der *handle_id* , der für **sp_kill_filestream_non_transacted_handles** erforderlich ist, bezieht sich nicht auf die session_id oder Arbeitseinheit, die in anderen **Kill** -Befehlen verwendet wird.  
  
 Weitere Informationen finden Sie unter [Verwalten von FileTables](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="metadata"></a>Metadaten  
 Um Informationen über geöffnete nicht transaktionale Datei Handles zu erhalten, Fragen Sie die dynamische Verwaltungs Sicht [sys. dm_filestream_non_transacted_handles &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)ab.  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Sie müssen über die **View Database State** -Berechtigung verfügen, um Datei Handles aus der dynamischen Verwaltungs Sicht **sys. dm_FILESTREAM_non_transacted_handles** zu erhalten und **sp_kill_filestream_non_transacted_handles**auszuführen.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen wird gezeigt, wie **sp_kill_filestream_non_transacted_handles** aufgerufen wird, um nicht transaktionale Datei Handles für FILETABLE-Daten zu schließen.  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable'  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable', @handle_id = 0xFFFAAADD  
```  
  
 Im folgenden Beispiel wird gezeigt, wie ein-Skript verwendet wird, um ein *handle_id* zu erhalten und zu schließen.  
  
```sql  
DECLARE @handle_id varbinary(16);  
DECLARE @table_name sysname;  
  
SELECT TOP 1 @handle_id = handle_id, @table_name = Object_name(table_id)  
FROM sys.dm_FILESTREAM_non_transacted_handles;  
  
EXEC sp_kill_filestream_non_transacted_handles @dbname, @table_name, @handle_id;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von FileTables](../../relational-databases/blob/manage-filetables.md)  
 [Dynamische Verwaltungs Sichten für FILESTREAM und FILETABLE (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
 <br>[FILESTREAM-und FILETABLE-Katalog Sichten (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
 <br>[sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  
