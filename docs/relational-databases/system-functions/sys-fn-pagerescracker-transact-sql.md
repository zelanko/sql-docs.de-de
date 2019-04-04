---
title: sys.fn_PageResCracker (Transact-SQL) | Microsoft Docs
description: Dokumentation für sys.fn_PageResCracker-Systemfunktion.
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
ms.openlocfilehash: 2fc7136b60dba47813b9942316ee6fdfbc64f307
ms.sourcegitcommit: fc1739be9b2735b2bb469979936e76ca2a3830f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2019
ms.locfileid: "58899706"
---
# <a name="sysfnpagerescracker-transact-sql"></a>sys.fn_PageResCracker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Gibt die `db_id`, `file_id`, und `page_id` für den angegebenen `page_resource` Wert. 
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
```  
sys.fn_PageResCracker ( page_resource )  
```  
  
## <a name="arguments"></a>Argumente  
*page_resource*    
Ist das hexadezimale 8-Byte-Format einer Seite Datenbankressource.
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|db_id|**ssNoversion**|Datenbank-ID|  
|file_id|**ssNoversion**|Datei-ID|  
|page_id|**ssNoversion**|Seiten-ID|  
  
## <a name="remarks"></a>Hinweise  
`sys.fn_PageResCracker` wird verwendet, um die hexadezimale 8-Byte-Darstellung einer Datenbankseite in ein Rowset zu konvertieren, die die ID der Datenbank, Datei-ID und Seiten-ID der Seite enthält.   

Erhalten Sie eine gültigen Seitenbereiche-Ressource aus der `page_resource` Spalte die [Sys. dm_exec_requests &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) dynamische verwaltungssicht oder [sys.sysprocesses &#40;&#41; ](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md) -Systemsicht ab. Wenn eine ungültige Ressource verwendet wird, und klicken Sie dann die Rückgabe NULL ist.  
Der primäre Verwendungszweck `sys.fn_PageResCracker` besteht darin, die Joins zwischen diesen Ansichten zu vereinfachen und die [sys.dm_db_page_info &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) dynamische Verwaltungsfunktion, um Informationen über die Seite, wie z. B. Abrufen der Objekt, zu dem er gehört.
  
## <a name="permissions"></a>Berechtigungen  
Die benutzeranforderungen `VIEW SERVER STATE` Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
Die `sys.fn_PageResCracker` Funktion kann verwendet werden, zusammen mit [sys.dm_db_page_info &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) Seite behandeln und im Zusammenhang mit Wartevorgänge blockieren in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Das folgende Skript ist ein Beispiel für die Verwendung dieser Funktionen zum Sammeln von Datenbankinformationen der Seite für alle aktiven Anforderungen, die zurzeit auf eine Art von Seitenressource warten. 
  
```sql  
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)  
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
