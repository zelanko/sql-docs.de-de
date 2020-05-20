---
title: sp_trace_setstatus (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_setstatus_TSQL
- sp_trace_setstatus
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setstatus
ms.assetid: 29e7a7d7-b9c1-414a-968a-fc247769750d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 98eaa39475b58c7fad5b20c4f6a65101d33b103d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82809716"
---
# <a name="sp_trace_setstatus-transact-sql"></a>sp_trace_setstatus (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert den aktuellen Status der angegebenen Ablaufverfolgung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen erweiterte Ereignisse.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_trace_setstatus [ @traceid = ] trace_id , [ @status = ] status  
```  
  
## <a name="arguments"></a>Argumente  
`[ @traceid = ] trace_id`Die ID der Ablauf Verfolgung, die geändert werden soll. *trace_id* ist vom Datentyp **int**und hat keinen Standardwert. Der Benutzer verwendet diesen *trace_id* Wert, um die Ablauf Verfolgung zu identifizieren, zu ändern und zu steuern. Weitere Informationen zum Abrufen des *trace_id*finden Sie unter [sys. fn_trace_getinfo &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md).  
  
`[ @status = ] status`Gibt die Aktion an, die für die Ablauf Verfolgung implementiert werden soll. *Status* ist vom Datentyp **int**und hat keinen Standardwert.  
  
 In der folgenden Tabelle sind die Status aufgelistet, die möglicherweise angegeben werden.  
  
|Status|BESCHREIBUNG|  
|------------|-----------------|  
|**0**|Beendet die angegebene Ablaufverfolgung.|  
|**1**|Startet die angegebene Ablaufverfolgung.|  
|**2**|Schließt die angegebene Ablaufverfolgung und löscht ihre Definition vom Server.|  
  
> [!NOTE]  
>  Eine Ablaufverfolgung muss beendet werden, bevor sie geschlossen werden kann. Eine Ablaufverfolgung muss beendet und geschlossen werden, bevor sie angezeigt werden kann.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 In der folgenden Tabelle werden die Codewerte beschrieben, die die Benutzer nach Abschluss der gespeicherten Prozedur möglicherweise erhalten.  
  
|Rückgabecode|BESCHREIBUNG|  
|-----------------|-----------------|  
|**0**|Kein Fehler.|  
|**1**|Unbekannter Fehler.|  
|**8**|Der angegebene Status ist ungültig.|  
|**9**|Das angegebene Ablauf Verfolgungs Handle ist ungültig.|  
|**13**|Nicht genügend Arbeitsspeicher. Wird zurückgegeben, wenn nicht genügend Arbeitsspeicher zum Ausführen der angegebenen Aktion verfügbar ist.|  
  
 Wenn die Ablauf Verfolgung bereits in dem angegebenen Zustand ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird **0**zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Parameter aller gespeicherten Prozeduren der SQL-Ablaufverfolgung (**sp_trace_xx**) haben eine strikte Typbindung. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
 Ein Beispiel zum Verwenden gespeicherter Prozeduren der Ablaufverfolgung finden Sie unter [Erstellen einer Ablaufverfolgung &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Benutzer müssen über die ALTER TRACE-Berechtigung verfügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. fn_trace_geteventinfo &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys. fn_trace_getfilterinfo &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [SQL-Ablaufverfolgung](../../relational-databases/sql-trace/sql-trace.md)  
  
  
