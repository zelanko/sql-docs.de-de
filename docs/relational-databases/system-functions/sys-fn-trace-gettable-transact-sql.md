---
title: Sys. fn_trace_gettable (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_gettable
- fn_trace_gettable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_trace_gettable function
- sys.fn_trace_gettable function
ms.assetid: c2590159-6ec5-4510-81ab-e935cc4216cd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a52a8482f56bb81f6d4436d8196a39e9e277ea7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689158"
---
# <a name="sysfntracegettable-transact-sql"></a>sys.fn_trace_gettable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den Inhalt mindestens einer Ablaufverfolgungsdatei in Tabellenform zurück.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen erweiterte Ereignisse.  
   
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_trace_gettable ( 'filename' , number_files )  
```  
  
## <a name="arguments"></a>Argumente  
 "*Filename*"  
 Gibt die erste Ablaufverfolgungsdatei an, die gelesen werden soll. *FileName* ist **nvarchar(256)**, hat keinen Standardwert.  
  
 *number_files*  
 Gibt die Anzahl der zu lesenden Rolloverdateien an. Diese Zahl umfasst auch die erste Datei im angegebenen *Filename*. *Number_files* ist ein **Int**.  
  
## <a name="remarks"></a>Hinweise  
 Wenn *Number_files* angegeben ist, als **Standard**, **Fn_trace_gettable** liest alle Rolloverdateien, bis das Ende der Ablaufverfolgung erreicht. **' fn_trace_gettable '** gibt eine Tabelle mit allen Spalten für die angegebene Ablaufverfolgung gültigen. Weitere Informationen finden Sie unter [Sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md).  
  
 Beachten Sie, dass die Fn_trace_gettable-Funktion keine Rolloverdateien lädt (Wenn diese Option angegeben wird, mithilfe der *Number_files* Argument), wenn der ursprüngliche Name der Ablaufverfolgungsdatei, die mit einem Unterstrich und einem numerischen Wert endet. (Dies gilt nicht für den Unterstrich und die Zahl, die beim Rollover automatisch angehängt werden.) Um das Problem zu umgehen, können Sie die Ablaufverfolgungsdateien umbenennen, um die Unterstriche im ursprünglichen Dateinamen zu entfernen. Wenn die ursprüngliche Datei heißt beispielsweise **Trace_Oct_5.trc** und die Rolloverdatei heißt **Trace_Oct_5_1.trc**, können Sie die Dateien umbenennen **TraceOct5.trc** und  **TraceOct5_1.trc**.  
  
 Diese Funktion kann eine Ablaufverfolgung lesen, die noch auf der Instanz aktiv ist, auf der sie ausgeführt wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER TRACE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-fntracegettable-to-import-rows-from-a-trace-file"></a>A. Verwenden von fn_trace_gettable zum Importieren von Zeilen aus einer Ablaufverfolgungsdatei  
 Im folgenden Beispiel wird `fn_trace_gettable` innerhalb der `FROM`-Klausel einer `SELECT...INTO`-Anweisung aufgerufen.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
### <a name="b-using-fntracegettable-to-return-a-table-with-an-identity-column-that-can-be-loaded-into-a-sql-server-table"></a>B. Verwenden von fn_trace_gettable zum Zurückgeben einer Tabelle mit einer IDENTITY-Spalte, die in eine SQL Server-Tabelle geladen werden kann  
 Im folgenden Beispiel wird die Funktion als Teil einer `SELECT...INTO`-Anweisung aufgerufen. Die Funktion gibt eine Tabelle mit einer `IDENTITY`-Spalte zurück, die in die `temp_trc`-Tabelle geladen werden kann.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENTITY(int, 1, 1) AS RowNumber, * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
