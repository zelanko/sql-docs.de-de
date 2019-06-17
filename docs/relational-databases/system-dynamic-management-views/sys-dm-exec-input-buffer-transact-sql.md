---
title: dm_exec_input_buffer (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_input_buffer
- sys.dm_exec_input_buffer _tsql
- dm_exec_input_buffer
- dm_exec_input_buffer_tsql
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_input_buffer dynamic management function
ms.assetid: fb34a560-bde9-4ad9-aa96-0d4baa4fc104
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8531f33f2d027eba14d4416e9138560b25ead20e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013135"
---
# <a name="sysdmexecinputbuffer-transact-sql"></a>sys.dm_exec_input_buffer (Transact-SQL)
[!INCLUDE[tsql-appliesto-2014sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2014sp2-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu Anweisungen, die mit einer Instanz von übermittelt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.dm_exec_input_buffer ( session_id , request_id )
```  
  
## <a name="arguments"></a>Argumente  
*session_id*  
Führt die Sitzungs-Id den Batch gesucht werden soll. *Sitzungs-ID* ist **Smallint**. *Sitzungs-ID* aus den folgenden dynamischen Verwaltungsobjekten abgerufen werden kann:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)   
  
*request_id*  
Die Anforderungs-ID von [Sys. dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md). *Request_id* ist **Int**.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**event_type**|**nvarchar(256)**|Der Typ des Ereignisses im Puffer für die angegebene Spid.|  
|**parameters**|**smallint**|Alle Parameter für die Anweisung bereitgestellt.|  
|**event_info**|**nvarchar(max)**|Der Text der Anweisung im Puffer für die angegebene Spid.|  
  
## <a name="permissions"></a>Berechtigungen  
 Auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], wenn der Benutzer die VIEW SERVER STATE-Berechtigung hat, sieht der Benutzer alle zurzeit ausgeführten Sitzungen in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, andernfalls sieht der Benutzer nur die aktuelle Sitzung.  
  
 Auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)], wenn der Benutzer Besitzer der Datenbank ist, sieht der Benutzer alle zurzeit ausgeführten Sitzungen auf den [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ist, andernfalls sieht der Benutzer nur die aktuelle Sitzung.  
  
## <a name="remarks"></a>Hinweise  
 Diese dynamische Verwaltungsfunktion kann in Verbindung mit Sys. dm_exec_sessions oder Sys. dm_exec_requests verwendet werden, durch praktische Übungen **CROSS APPLY**.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-simple-example"></a>A. Einfaches Beispiel  
 Das folgende Beispiel zeigt eine Sitzungs-Id (SPID) und eine Anforderungs-Id an die Funktion übergeben.  
  
```sql  
SELECT * FROM sys.dm_exec_input_buffer (52, 0);
GO
```  
  
### <a name="b-using-cross-apply-to-additional-information"></a>B. Mithilfe der kreuzvalidierung gelten für zusätzliche Informationen  
 Im folgende Beispiel werden den Eingabepuffer für Sitzungen mit der Sitzungs-Id, die größer als 50 aufgelistet.  
  
```sql  
SELECT es.session_id, ib.event_info   
FROM sys.dm_exec_sessions AS es  
CROSS APPLY sys.dm_exec_input_buffer(es.session_id, NULL) AS ib  
WHERE es.session_id > 50;
GO
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführung bezogene dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [DBCC INPUTBUFFER &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)  
