---
description: snapshots.fn_trace_getdata (Transact-SQL)
title: Momentaufnahmen. fn_trace_getdata (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: f022a27c8a8e47cd12994d0d03ddb5af9a2f920c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464775"
---
# <a name="snapshotsfn_trace_getdata-transact-sql"></a>snapshots.fn_trace_getdata (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Diese Funktion gibt alle Ereignisse zurück, die für die angegebene Ablaufverfolgung aufgezeichnet wurden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
snapshots.fn_trace_gettable ( trace_info_id, start_time, end_time )  
```  
  
## <a name="arguments"></a>Argumente  
 *trace_info_id*  
 Der eindeutige Bezeichner für den Primärschlüssel in der Momentaufnahme. trace_info Tabelle in der Verwaltungs Data Warehouse Datenbank. *trace_info_id* ist **int**  
  
 *start_time*  
 Die Zeit, zu der die Ablaufverfolgung gestartet wurde. *start_time* ist **datetime**  
  
 *end_time*  
 Die Zeit, zu der die Ablaufverfolgung beendet wurde. *end_time* ist **datetime**  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|\<All trace columns>|\<Varies>|Die Ablaufverfolgungsdaten aus der Tabelle snapshots.trace_data in der Verwaltungs-Data Warehouse-Datenbank.<br /><br /> Mithilfe der folgenden Abfrage kann eine Liste der Spalten für die angegebene Ablaufverfolgung abgerufen werden:<br /><br /> `SELECT * FROM sys.trace_columns`<br /><br /> **Hinweis:** Die Spalten, die von der Momentaufnahmen. fn_trace_gettable-Funktion zurückgegeben werden, entsprechen den Werten in der Spalte "Name" in der Systemsicht sys. trace_columns. Der einzige Unterschied ist, dass die Spalte GroupID von der Funktion nicht zurückgegeben wird.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die SELECT-Berechtigung für mdw_reader.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
