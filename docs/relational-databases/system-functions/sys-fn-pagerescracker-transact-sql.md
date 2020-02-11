---
title: sys. fn_PageResCracker (Transact-SQL) | Microsoft-Dokumentation
description: Dokumentation für die Systemfunktion sys. fn_PageResCracker.
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
ms.openlocfilehash: 6d8203979a0afdca1ae78b9bd51723c906c40ea2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68267075"
---
# <a name="sysfn_pagerescracker-transact-sql"></a>sys. fn_PageResCracker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Gibt `db_id`, `file_id`und `page_id` für den angegebenen `page_resource` Wert zurück. 
  
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

Sie können eine gültige Seiten Ressource aus der `page_resource` Spalte der [sys. dm_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) dynamische Verwaltungs Sicht oder [sys. sysprocesses &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md) Systemsicht abrufen. Wenn eine ungültige Seiten Ressource verwendet wird, ist die Rückgabe NULL.  
Der primäre Verwendungszweck `sys.fn_PageResCracker` von besteht darin, Joins zwischen diesen Sichten und der dynamischen Verwaltungsfunktion [sys. dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) zu vereinfachen, um Informationen über die Seite zu erhalten, z. b. das Objekt, zu dem Sie gehört.
  
## <a name="permissions"></a>Berechtigungen  
Der Benutzer benötigt `VIEW SERVER STATE` die-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
Die `sys.fn_PageResCracker` -Funktion kann zusammen mit [sys. dm_db_page_info &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) verwendet werden, um die Behandlung von seitenbezogenen Warte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Vorgängen und Blockierungen in zu beheben.  Das folgende Skript ist ein Beispiel dafür, wie Sie diese Funktionen verwenden können, um Datenbankseiten Informationen für alle aktiven Anforderungen zu sammeln, die zurzeit auf eine Art von Seiten Ressource warten. 
  
```sql  
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_db_page_info &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)  
 [sys. sysprocesses &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
