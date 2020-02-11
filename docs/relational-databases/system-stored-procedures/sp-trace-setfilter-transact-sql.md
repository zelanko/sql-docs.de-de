---
title: sp_trace_setfilter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_setfilter
- sp_trace_setfilter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setfilter
ms.assetid: 11e7c7ac-a581-4a64-bb15-9272d5c1f7ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f48f7e8dd6e7d8fa57868994f9bcabb66777e90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68095940"
---
# <a name="sp_trace_setfilter-transact-sql"></a>sp_trace_setfilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wendet einen Filter auf eine Ablaufverfolgung an. **sp_trace_setfilter** werden möglicherweise nur für vorhandene Ablauf Verfolgungen ausgeführt, die beendet wurden (*Status* ist **0**). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Gibt einen Fehler zurück, wenn diese gespeicherte Prozedur für eine Ablauf Verfolgung ausgeführt wird, die nicht vorhanden ist oder deren *Status* nicht **0**ist.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen erweiterte Ereignisse.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_trace_setfilter [ @traceid = ] trace_id   
          , [ @columnid = ] column_id  
          , [ @logical_operator = ] logical_operator  
          , [ @comparison_operator = ] comparison_operator  
          , [ @value = ] value  
```  
  
## <a name="arguments"></a>Argumente  
`[ @traceid = ] trace_id`Die ID der Ablauf Verfolgung, für die der Filter festgelegt ist. *trace_id* ist vom Datentyp **int**und hat keinen Standardwert. Der Benutzer verwendet diesen *trace_id* Wert, um die Ablauf Verfolgung zu identifizieren, zu ändern und zu steuern.  
  
`[ @columnid = ] column_id`Die ID der Spalte, auf die der Filter angewendet wird. *column_id* ist vom Datentyp **int**und hat keinen Standardwert. Wenn *column_id* NULL ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden alle Filter für die angegebene Ablauf Verfolgung gelöscht.  
  
`[ @logical_operator = ] logical_operator`Gibt an, ob der and (**0**) or or (**1**)-Operator angewendet wird. *logical_operator* ist vom Datentyp **int**und hat keinen Standardwert.  
  
`[ @comparison_operator = ] comparison_operator`Gibt den Typ des Vergleichs an, der erstellt werden soll. *comparison_operator* ist vom Datentyp **int**und hat keinen Standardwert. Die folgende Tabelle enthält die Vergleichsoperatoren und die sie darstellenden Werte.  
  
|value|Vergleichsoperator|  
|-----------|-------------------------|  
|**0**|= (Gleich)|  
|**1**|<>  (nicht gleich)|  
|**2**|> (Größer als)|  
|**€**|< (Kleiner als)|  
|**4**|>= (größer als oder gleich)|  
|**5@@**|<= (kleiner als oder gleich)|  
|**6**|LIKE|  
|**19.00**|Nicht wie|  
  
`[ @value = ] value`Gibt den Wert an, nach dem gefiltert werden soll. Der Datentyp des *Werts* muss mit dem Datentyp der zu filternden Spalte identisch sein. Wenn der Filter beispielsweise für eine Objekt-ID-Spalte mit einem **int** -Datentyp festgelegt ist, muss *value* " **int**" lauten. Wenn ** der Wert **nvarchar** oder **varbinary**ist, kann er eine maximale Länge von 8000 aufweisen.  
  
 Wenn der Vergleichsoperator LIKE oder NOT LIKE ist, kann der logische Operator % oder einen anderen für die LIKE-Operation geeigneten Filter enthalten.  
  
 Sie können NULL als *Wert* angeben, um Ereignisse mit NULL-Spaltenwerten herauszufiltern. Nur die Operatoren **0** (= gleich) und **1** (<> nicht gleich) sind mit NULL gültig. In diesem Fall entsprechen diese Operatoren den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Operatoren IS NULL und IS NOT NULL.  
  
 Um den Filter zwischen einem Bereich von Spaltenwerten anzuwenden, müssen **sp_trace_setfilter** zweimal ausgeführt werden, einmal mit einem größer-als-oder-gleich-Vergleichs Operator (' >= ') und einem anderen Zeitpunkt mit einem kleiner-als-oder-gleich-Operator (' <= ').  
  
 Weitere Informationen zu Datenspalten Datentypen finden Sie in der [SQL Server-Ereignis Klassenreferenz](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 In der folgenden Tabelle werden die Codewerte beschrieben, die die Benutzer nach Abschluss der gespeicherten Prozedur möglicherweise erhalten.  
  
|Rückgabecode|BESCHREIBUNG|  
|-----------------|-----------------|  
|0|Kein Fehler.|  
|1|Unknown error. (Unbekannter Fehler.)|  
|2|Die Ablaufverfolgung wird derzeit ausgeführt. Das Ändern der Ablauf Verfolgung zu diesem Zeitpunkt führt zu einem Fehler.|  
|4|Die angegebene Spalte ist ungültig.|  
|5|Für die angegebene Spalte ist das Filtern nicht zulässig. Dieser Wert wird nur von **sp_trace_setfilter**zurückgegeben.|  
|6|Der angegebene Vergleichsoperator ist ungültig.|  
|7|Der angegebene logische Operator ist ungültig.|  
|9|Das angegebene Ablauf Verfolgungs Handle ist ungültig.|  
|13|Nicht genügend Arbeitsspeicher. Wird zurückgegeben, wenn nicht genügend Arbeitsspeicher zum Ausführen der angegebenen Aktion verfügbar ist.|  
|16|Die Funktion ist für diese Ablaufverfolgung ungültig.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_trace_setfilter** ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Prozedur, die viele der Aktionen ausführt, die zuvor von erweiterten gespeicherten Prozeduren ausgeführt wurden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die in früheren Versionen von verfügbar waren. Verwenden Sie **sp_trace_setfilter** anstelle des **xp_trace_set\*Filtern** Sie erweiterte gespeicherte Prozeduren, um Filter für Ablauf Verfolgungen zu erstellen, anzuwenden, zu entfernen oder zu bearbeiten. Weitere Informationen finden Sie unter [Filtern einer Ablauf Verfolgung](../../relational-databases/sql-trace/filter-a-trace.md).  
  
 Alle Filter für eine bestimmte Spalte müssen in einer Ausführung von **sp_trace_setfilter**miteinander aktiviert werden. Wenn ein Benutzer z. B. zwei Filter auf die Spalte application name und einen Filter auf die Spalte username anwenden möchte, muss er die Filter für application name nacheinander angeben. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt einen Fehler zurück, wenn der Benutzer in einem Aufruf einer gespeicherten Prozedur einen Filter für application name angibt und danach ein Filter für username und ein weiterer Filter für application name folgt.  
  
 Parameter aller gespeicherten Prozeduren der SQL-Ablaufverfolgung (**sp_trace_xx**) haben eine strikte Typbindung. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Benutzer müssen über die ALTER TRACE-Berechtigung verfügen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden drei Filter für die Ablaufverfolgung `1` festgelegt. Die Filter `N'SQLT%'` und `N'MS%'` werden mithilfe des Vergleichsoperators "`AppName`" für eine Spalte (`10`, Wert `LIKE`) verwendet. Der `N'joe'`-Filter wird mithilfe des Vergleichsoperators "`UserName`" für eine andere Spalte (`11`, Wert `EQUAL`) verwendet.  
  
```  
sp_trace_setfilter  1, 10, 0, 6, N'SQLT%';  
sp_trace_setfilter  1, 10, 0, 6, N'MS%';  
sp_trace_setfilter  1, 11, 0, 0, N'joe';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [SQL-Ablaufverfolgung](../../relational-databases/sql-trace/sql-trace.md)  
  
  
