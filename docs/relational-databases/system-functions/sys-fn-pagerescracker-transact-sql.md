---
title: sys. fn_PageResCracker (Transact-SQL) | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Systemfunktion sys. fn_PageResCracker. Weitere Informationen finden Sie unter Beispiele und Anzeigen zusätzlicher Ressourcen.
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_PageResCracker
- sys.fn_PageResCracker_TSQL
- fn_PageResCracker_TSQL
- sys.fn_PageResCracker
- sys.dm_db_page_info
dev_langs:
- TSQL
helpviewer_keywords:
- fn_PageResCracker function
- page_resource
- sys.fn_PageResCracker function
- sys.dm_db_page_info
- page info
author: bluefooted
ms.author: pamela
manager: amitban
ms.openlocfilehash: a48b5ba06223130a83980bf6cf8ec410bd58e5a1
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247579"
---
# <a name="sysfn_pagerescracker-transact-sql"></a>sys. fn_PageResCracker (Transact-SQL)
[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Gibt `db_id` , `file_id` und `page_id` für den angegebenen Wert zurück `page_resource` . 
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
```  
sys.fn_PageResCracker ( page_resource )  
```  
  
## <a name="arguments"></a>Argumente  
*page_resource*    
Das 8-Byte-Hexadezimal Format einer Datenbankseiten Ressource.
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|db_id|**int**|Datenbank-ID|  
|file_id|**int**|Datei-ID|  
|page_id|**int**|Seiten-ID|  
  
## <a name="remarks"></a>Bemerkungen  
`sys.fn_PageResCracker`wird verwendet, um die hexadezimale 8-Byte-Darstellung einer Datenbankseite in ein Rowset zu konvertieren, das die Datenbank-ID, die Datei-ID und die Seiten-ID der Seite enthält.   

Sie können eine gültige Seiten Ressource aus der `page_resource` Spalte der dynamischen Verwaltungs Sicht [sys. dm_exec_requests &#40;Transact-&#41;SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) oder der [sys.sysProzesse &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md) Systemansicht abrufen. Wenn eine ungültige Seiten Ressource verwendet wird, ist die Rückgabe NULL.  
Der primäre Verwendungszweck von besteht darin, `sys.fn_PageResCracker` Joins zwischen diesen Sichten und der dynamischen Verwaltungsfunktion [sys. dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) zu vereinfachen, um Informationen über die Seite zu erhalten, z. b. das Objekt, zu dem Sie gehört.
  
## <a name="permissions"></a>Berechtigungen  
Der Benutzer benötigt die- `VIEW SERVER STATE` Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
Die- `sys.fn_PageResCracker` Funktion kann zusammen mit [sys. dm_db_page_info &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) verwendet werden, um die Behandlung von seitenbezogenen warte Vorgängen und Blockierungen in zu beheben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Das folgende Skript ist ein Beispiel dafür, wie Sie diese Funktionen verwenden können, um Datenbankseiten Informationen für alle aktiven Anforderungen zu sammeln, die zurzeit auf eine Art von Seiten Ressource warten. 
  
```sql  
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_db_page_info &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)  
 [sys.sysProzesse &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
