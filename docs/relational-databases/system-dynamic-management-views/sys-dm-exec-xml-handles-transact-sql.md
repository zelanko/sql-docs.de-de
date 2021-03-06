---
description: sys.dm_exec_xml_handles (Transact-SQL)
title: sys.dm_exec_xml_handles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_xml_handles
- dm_exec_xml_handles_TSQL
- sys.dm_exec_xml_handles_TSQL
- sys.dm_exec_xml_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_xml_handles dynamic management function
ms.assetid: a873ce0f-6955-417a-96a1-b2ef11a83633
author: pmasl
ms.author: pelopes
monikerRange: =azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0433126f43a14aa12521c0a65cd1b4aca8441ac6
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482661"
---
# <a name="sysdm_exec_xml_handles-transact-sql"></a>sys.dm_exec_xml_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Gibt Informationen zu aktiven Handles zurück, die von **sp_xml_preparedocument** geöffnet wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dm_exec_xml_handles (session_id | 0 )  
```  
  
## <a name="arguments"></a>Argumente  
 *session_id* | 1,0  
 ID der Sitzung. Wenn *session_id* angegeben wird, gibt die Funktion Informationen zu XML-Handles in der angegebenen Sitzung zurück.  
  
 Wenn 0 angegeben wird, gibt die Funktion Informationen zu allen XML-Handles für alle Sitzungen zurück.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Sitzungs-ID der Sitzung, die dieses XML-Dokumenthandle verwaltet.|  
|**document_id**|**int**|Von **sp_xml_preparedocument** zurückgegebene ID eines XML-Dokumenthandles.|  
|**namespace_document_id**|**int**|Interne Handle-ID für das zugeordnete Namespacedokument, das als dritter Parameter an **sp_xml_preparedocument** übergeben wurde. NULL, wenn kein Namespacedokument vorhanden ist.|  
|**sql_handle**|**varbinary(64)**|Handle für den Text des SQL-Codes, in dem das Handle definiert wurde.|  
|**statement_start_offset**|**int**|Die Anzahl von Zeichen, nach der der Aufruf von **sp_xml_preparedocument** im zurzeit ausgeführten Batch oder in der gespeicherten Prozedur auftritt. Kann mit dem **sql_handle**, dem **statement_end_offset** und der dynamischen Verwaltungsfunktion **sys.dm_exec_sql_text** zum Abrufen der aktuell ausgeführten Anweisung für die Anforderung verwendet werden.|  
|**statement_end_offset**|**int**|Die Anzahl von Zeichen, nach der der Aufruf von **sp_xml_preparedocument** im zurzeit ausgeführten Batch oder in der gespeicherten Prozedur auftritt. Kann zusammen mit **sql_handle**, **statement_start_offset** und der dynamischen Verwaltungsfunktion **sys.dm_exec_sql_text** zum Abrufen der zurzeit ausgeführten Anweisung für die Anforderung verwendet werden.|  
|**creation_time**|**datetime**|Timestamp des Aufrufs von **sp_xml_preparedocument** .|  
|**original_document_size_bytes**|**bigint**|Größe des nicht analysierten XML-Dokuments in Bytes.|  
|**original_namespace_document_size_bytes**|**bigint**|Größe des nicht analysierten XML-Namespacedokuments in Bytes. NULL, wenn kein Namespacedokument vorhanden ist.|  
|**num_openxml_calls**|**bigint**|Die Anzahl von OPENXML-Aufrufen mit diesem Dokumenthandle.|  
|**row_count**|**bigint**|Die Anzahl von Zeilen, die von allen vorherigen OPENXML-Aufrufen für dieses Dokumenthandle zurückgegeben wurden.|  
|**dormant_duration_ms**|**bigint**|Millisekunden seit dem letzten OPENXML-Aufruf. Falls OPENXML nicht aufgerufen wurde, werden die Millisekunden seit dem Aufruf von **sp_xml_preparedocument** zurückgegeben.|  
  
## <a name="remarks"></a>Hinweise  
 Die Lebensdauer von **sql_handle** -Werten, mit denen der SQL-Text abgerufen wird, in dem ein Aufruf von **sp_xml_preparedocument** ausgeführt wird, überdauert den zwischengespeicherten Plan, nach dem die Abfrage ausgeführt wird. Ist der Abfragetext nicht im Cache verfügbar, können die Daten nicht mithilfe der Informationen im Funktionsergebnis abgerufen werden. Dies kann eintreten, wenn Sie viele umfangreiche Batches ausführen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server, um alle Sitzungen oder Sitzungs-IDs anzuzeigen, die nicht im Besitz des Aufrufers sind. Ein Aufrufer kann immer die Daten für seine eigene aktuelle Sitzungs-ID anzeigen.      
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle aktiven Handles ausgewählt.  
  
```  
SELECT * FROM sys.dm_exec_xml_handles(0);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <br>[Dynamische Verwaltungs Sichten und-Funktionen (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
 <br>[Dynamische Verwaltungs Sichten und-Funktionen im Zusammenhang mit der Ausführung (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)
 <br>[sp_xml_preparedocument (Transact-SQL)](../system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[sp_xml_removedocument (Transact-SQL)](../system-stored-procedures/sp-xml-removedocument-transact-sql.md)


 
  
  
