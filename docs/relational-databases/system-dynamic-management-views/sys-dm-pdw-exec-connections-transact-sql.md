---
title: sys. dm_pdw_exec_connections (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b333af29e3d39c0f4ce59ea68602f652c042003f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899419"
---
# <a name="sysdm_pdw_exec_connections-transact-sql"></a>sys. dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Gibt Informationen über die zu dieser Instanz von [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] hergestellten Verbindungen zurück, sowie Details zu jeder der Verbindungen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Identifiziert die Sitzung, die dieser Verbindung zugeordnet ist. Verwenden `SESSION_ID()` Sie, um `session_id` den der aktuellen Verbindung zurückzugeben.|  
|connect_time|**datetime**|Zeitstempel, der angibt, wann die Verbindung eingerichtet wurde. Lässt keine NULL-Werte zu.|  
|encrypt_option|**nvarchar(40)**|Gibt true (die Verbindung ist verschlüsselt) oder false (die Verbindung ist nicht "tctypred").|  
|auth_scheme|**nvarchar(40)**|Gibt das mit dieser Verbindung verwendete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-/Windows-Authentifizierungsschema an. Lässt keine NULL-Werte zu.|  
|client_id|**varchar(48)**|Die IP-Adresse des Clients, der eine Verbindung mit diesem Server herstellt. Lässt NULL-Werte zu.|  
|sql_spid|**int**|Die Server Prozess-ID der Verbindung. Verwenden `@@SPID` Sie, um `sql_spid` den der aktuellen Verbindung zurückzugeben. Verwenden Sie für den spezifischsten Zweck `session_id` stattdessen den.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **View Server State** -Berechtigung auf dem Server.  
  
## <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions. session_id|dm_pdw_exec_connections. session_id|1:1|  
|dm_pdw_exec_requests. connection_id|dm_pdw_exec_connections. connection_id|n:1|  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Typische Abfrage zum Sammeln von Informationen über die eigene Verbindung einer Abfrage.  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

