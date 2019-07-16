---
title: Sys.fn_MSxe_read_event_stream (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_MSxe_read_event_stream_TSQL
- sys.fn_MSxe_read_event_stream_TSQL
- sys.fn_MSxe_read_event_stream
- fn_MSxe_read_event_stream
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_MSxe_read_event_stream
- fn_MSxe_read_event_stream
ms.assetid: 5edb1162-625a-41e0-8ec9-1edc8ab9a74a
author: rothja
ms.author: jroth
ms.openlocfilehash: 886b874aeee47f71eb8b50dba27fdfdf8ea45c62
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082693"
---
# <a name="sysfnmsxereadeventstream-transact-sql"></a>sys.fn_MSxe_read_event_stream (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Erweiterte Ereignisse stellen eine Tabellenwertfunktion (Table Valued Function, TVF) zur internen Verwendung in der Benutzeroberfläche für erweiterte Ereignisse bereit. Die Tabelle enthält keine verwendbaren Kundendaten.  
  
 Sie können die Ereignisdaten mit einer der folgenden Methoden anzeigen:  
  
-   Benutzeroberfläche für eine neue Sitzung mit erweiterten Ereignissen.  
  
-   fn_xe_file_target_read_file TVF. Weitere Informationen finden Sie unter [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql.md).  
  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_MSxe_read_event_stream ( session_name)  
```  
  
## <a name="arguments"></a>Argumente  
 *Sitzungsname*  
 Der Name einer Sitzung, die auf dem Server ausgeführt wird.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|Typ|**Ganze Zahl (4)**|Der Ereignistyp. Lässt keine NULL-Werte zu.|  
|data|**Bild (16)**|Die Bilddaten des Ereignisses. Lässt NULL-Werte zu.|  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten für erweiterte Ereignisse](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Katalogsichten für erweiterte Ereignisse &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
