---
title: sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- sp_estimated_rowsize_reduction_for_vardecimal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- decimal data type, compressing
- numeric data type, compressing
- estimate decimal compression
- table compression [SQL Server]
ms.assetid: 0fe45983-f9f2-4c7f-938a-0fd96e1cbe8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90de7b95febdf2f1a25a5e584b2ca77bb67f93d4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124511"
---
# <a name="sp_estimated_rowsize_reduction_for_vardecimal-transact-sql"></a>sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Schätzt die Verringerung der durchschnittlichen Zeilengröße ab, wenn Sie das vardecimal-Speicherformat für eine Tabelle aktivieren. Verwenden Sie diese Zahl, um die Gesamtverringerung der Tabellengröße abzuschätzen. Da zur Berechnung der durchschnittlichen Verringerung der Zeilengröße die Stichprobenuntersuchung verwendet wird, betrachten Sie dies nur als Schätzung. In seltenen Fällen kann sich die Zeilengröße erhöhen, nachdem Sie das vardecimal-Speicherformat aktiviert haben.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen die ROW-Komprimierung und die PAGE-Komprimierung. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md). Informationen zur Komprimierung der Größe von Tabellen und Indizes finden Sie unter [sp_estimate_data_compression_savings &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_estimated_rowsize_reduction_for_vardecimal [ [ @table_name = ] 'table'] [;]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table = ] 'table'`Der dreiteilige Name der Tabelle, für die das Speicherformat geändert werden soll. *Table ist vom Datentyp* **nvarchar (776)**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Das folgende Resultset wird zurückgegeben, damit Informationen zur aktuellen und geschätzten Tabellengröße bereitgestellt werden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**avg_rowlen_fixed_format**|**Dezimalzahl (12, 2)**|Stellt die Länge der Zeile im festen Dezimalspeicherformat dar.|  
|**avg_rowlen_vardecimal_format**|**Dezimalzahl (12, 2)**|Stellt die durchschnittliche Zeilengröße dar, wenn das vardecimal-Speicherformat verwendet wird.|  
|**row_count**|**int**|Anzahl der Zeilen in der Tabelle|  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie **sp_estimated_rowsize_reduction_for_vardecimal** , um die Einsparungen zu schätzen, die sich ergeben, wenn Sie eine Tabelle für das vardecimal--Speicherformat aktivieren. Wenn beispielsweise die durchschnittliche Größe der Zeile um 40 % verringert werden kann, können Sie die Größe der Tabelle potenziell um 40 % verringern. Möglicherweise erhalten Sie keine Platzeinsparung; dies hängt vom Füllfaktor und von der Zeilengröße ab. Wenn es sich beispielsweise um eine Zeile handelt, die 8000 Bytes lang ist, und Sie die Größe um 40 % verringern, passt weiterhin nur eine Zeile auf eine Datenseite, was zu keiner Einsparung führt.  
  
 Wenn die Ergebnisse von **sp_estimated_rowsize_reduction_for_vardecimal** die angeben, dass die Tabelle vergrößert wird, bedeutet dies, dass viele Zeilen in der Tabelle fast die gesamte Genauigkeit der Dezimal Datentypen verwenden, und dass der für das vardecimal--Speicherformat erforderliche kleinere Verwaltungsaufwand größer ist als die Einsparung aus dem vardecimal--Speicherformat. Aktivieren Sie in diesem seltenen Fall das vardecimal-Speicherformat nicht.  
  
 Wenn eine Tabelle für das vardecimal--Speicherformat aktiviert ist, verwenden Sie **sp_estimated_rowsize_reduction_for_vardecimal** , um die durchschnittliche Größe der Zeile zu schätzen, wenn das vardecimal--Speicherformat deaktiviert ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für die Tabelle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Verringerung der Zeilengröße abgeschätzt, wenn die `Production.WorkOrderRouting`-Tabelle in der `AdventureWorks2012`-Datenbank komprimiert wird.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimated_rowsize_reduction_for_vardecimal 'Production.WorkOrderRouting' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_db_vardecimal_storage_format &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)   
 [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
