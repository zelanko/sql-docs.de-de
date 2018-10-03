---
title: Snapshots. fn_trace_getdata (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- snapshots.fn_trace_getdata
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots.fn_trace_getdata function
ms.assetid: ac28ef48-f4f4-4bf2-ba22-d44e1be88172
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 525d33568170543538473d403985ff8cb8b54c30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47743258"
---
# <a name="snapshotsfntracegetdata-transact-sql"></a>snapshots.fn_trace_getdata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Funktion gibt alle Ereignisse zurück, die für die angegebene Ablaufverfolgung aufgezeichnet wurden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
snapshots.fn_trace_gettable ( trace_info_id, start_time, end_time )  
```  
  
## <a name="arguments"></a>Argumente  
 *trace_info_id*  
 Der eindeutige Bezeichner für den Primärschlüssel in der Tabelle trace_info in der Verwaltungs-Data warehouse-Datenbank. *trace_info_id* ist **int**  
  
 *start_time*  
 Die Zeit, zu der die Ablaufverfolgung gestartet wurde. *start_time* ist **datetime**  
  
 *end_time*  
 Die Zeit, zu der die Ablaufverfolgung beendet wurde. *end_time* ist **datetime**  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|\<Verfolgen Sie alle Spalten >|\<Variiert nach >|Die Ablaufverfolgungsdaten aus der Tabelle snapshots.trace_data in der Verwaltungs-Data Warehouse-Datenbank.<br /><br /> Mithilfe der folgenden Abfrage kann eine Liste der Spalten für die angegebene Ablaufverfolgung abgerufen werden:<br /><br /> `SELECT * FROM sys.trace_columns`<br /><br /> **Hinweis:** entsprechen die Spalten, die von der fn_trace_gettable-Funktion zurückgegeben werden die Werte in der Spalte "Name" in der trace_columns-Systemsicht. Der einzige Unterschied ist, dass die Spalte GroupID von der Funktion nicht zurückgegeben wird.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die SELECT-Berechtigung für mdw_reader.  
  
## <a name="see-also"></a>Siehe auch  
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
