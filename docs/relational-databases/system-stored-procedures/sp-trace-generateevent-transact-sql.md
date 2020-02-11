---
title: sp_trace_generateevent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_generateevent_TSQL
- sp_trace_generateevent
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_generateevent
ms.assetid: 3ef05bfb-b467-4403-89cc-6e77ef9247dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: cfeacf9f3c18d3f80b7ad83a3697e33a5797ba22
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096023"
---
# <a name="sp_trace_generateevent-transact-sql"></a>sp_trace_generateevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt ein benutzerdefiniertes Ereignis in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
>**Hinweis:**  Diese gespeicherte Prozedur ist **nicht** als veraltet markiert. Alle anderen ablaufverfolgungsbezogenen gespeicherten Prozeduren sind veraltet.  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_trace_generateevent [ @eventid = ] event_id   
     [ , [ @userinfo = ] 'user_info' ]  
     [ , [ @userdata = ] user_data ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @eventid = ] event_id`Die ID des Ereignisses, das aktiviert werden soll. *event_id* ist vom Datentyp **int**und hat keinen Standardwert. Die ID muss eine der Ereignisnummern von 82 bis 91 sein, die mit [sp_trace_setevent](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)festgelegte benutzerdefinierte Ereignisse darstellen.  
  
`[ @userinfo = ] 'user_info'`Die optionale benutzerdefinierte Zeichenfolge, die den Grund für das Ereignis identifiziert. *user_info* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL.  
  
`[ @userdata = ] user_data`Die optionalen benutzerdefinierten Daten für das Ereignis. *user_data* ist vom Datentyp **varbinary (8000)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 In der folgenden Tabelle werden die Codewerte beschrieben, die die Benutzer nach Abschluss der gespeicherten Prozedur möglicherweise erhalten.  
  
|Rückgabecode|BESCHREIBUNG|  
|-----------------|-----------------|  
|**0**|Kein Fehler.|  
|**1**|Unknown error. (Unbekannter Fehler.)|  
|**€**|Das angegebene Ereignis ist ungültig. Das Ereignis ist möglicherweise nicht vorhanden oder nicht für die gespeicherte Prozedur geeignet.|  
|**13,3**|Nicht genügend Arbeitsspeicher. Wird zurückgegeben, wenn nicht genügend Arbeitsspeicher zum Ausführen der angegebenen Aktion verfügbar ist.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_trace_generateevent** führt viele der Aktionen aus, die zuvor von **den\* xp_trace_** erweiterten gespeicherten Prozeduren ausgeführt wurden. Verwenden Sie **sp_trace_generateevent** anstelle von **xp_trace_generate_event**.  
  
 Mit **sp_trace_generateevent**können nur die ID-Nummern von benutzerdefinierten Ereignissen verwendet werden. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird ein Fehler ausgelöst, wenn andere Ereignis-ID-Nummern verwendet werden.  
  
 Parameter aller gespeicherten Prozeduren der SQL-Ablaufverfolgung (**sp_trace_xx**) haben eine strikte Typbindung. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Benutzer müssen über die ALTER TRACE-Berechtigung verfügen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein vom Benutzer konfigurierbares Ereignis in einer Beispieltabelle erstellt.  
  
```  
--Create a sample table.  
CREATE TABLE user_config_test(col1 int, col2 char(10));  
  
--DROP the trigger if it already exists.  
IF EXISTS  
   (SELECT * FROM sysobjects WHERE name = 'userconfig_trg')  
   DROP TRIGGER userconfig_trg;  
  
--Create an ON INSERT trigger on the sample table.  
CREATE TRIGGER userconfig_trg  
   ON user_config_test FOR INSERT;  
AS  
EXEC master..sp_trace_generateevent  
   @event_class = 82, @userinfo = N'Inserted row into user_config_test';  
  
--When an insert action happens, the user-configurable event fires. If   
you were capturing the event id=82, you will see it in the Profiler output.  
INSERT INTO user_config_test VALUES(1, 'abc');  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. fn_trace_geteventinfo &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [SQL-Ablaufverfolgung](../../relational-databases/sql-trace/sql-trace.md)  
  
  
