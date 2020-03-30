---
title: TRIGGER_NESTLEVEL (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TRIGGER_NESTLEVEL
- TRIGGER_NESTLEVEL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- triggers [SQL Server], number executed
- number of triggers
- TRIGGER_NESTLEVEL function
ms.assetid: 6a33e74a-0cf9-4ae1-a1e4-4a137a3ea39d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6215824f230001cb9d7add20d32c85780a65ede6
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68098814"
---
# <a name="trigger_nestlevel-transact-sql"></a>TRIGGER_NESTLEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die Anzahl von Triggern zurück, die für die Anweisung ausgelöst wurden, von der der Trigger ausgeführt wurde. TRIGGER_NESTLEVEL wird in DML- und DDL-Triggern verwendet, um die aktuelle Schachtelungsebene zu bestimmen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TRIGGER_NESTLEVEL ( [ object_id ] , [ 'trigger_type' ] , [ 'trigger_event_category' ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *object_id*  
 Die Objekt-ID eines Triggers. Wenn *object_id* angegeben wird, wird die Häufigkeit zurückgegeben, mit der der angegebene Trigger für die Anweisung ausgeführt wurde. Wenn *object_id* nicht angegeben wird, wird die Häufigkeit zurückgegeben, mit der alle Trigger für die Anweisung ausgeführt wurden.  
  
 **'** *trigger_type* **'**  
 Gibt an, ob TRIGGER_NESTLEVEL auf AFTER- oder INSTEAD OF-Trigger angewendet werden soll. Geben Sie **AFTER** für AFTER-Trigger an. Geben Sie **IOT** für INSTEAD OF-Trigger an. Wenn *trigger_type* angegeben ist, muss auch *trigger_event_category* angegeben sein.  
  
 **'** *trigger_event_category* **'**  
 Gibt an, ob TRIGGER_NESTLEVEL auf DML- oder DDL-Trigger angewendet werden soll. Geben Sie **DML** für DML-Trigger an. Geben Sie **DDL** für DDL-Trigger an. Wenn *trigger_event_category* angegeben ist, muss auch *trigger_type* angegeben sein. Beachten Sie, dass nur **AFTER** für **DDL** angegeben werden kann, weil DDL-Trigger nur AFTER-Trigger sein können.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn keine Parameter angegeben werden, gibt TRIGGER_NESTLEVEL die Gesamtanzahl von Triggern in der Aufrufliste zurück. Der Parameter selbst ist ebenfalls darin eingeschlossen. Es kann vorkommen, dass Parameter nicht angegeben werden, wenn ein Trigger Befehle ausführt, die das Auslösen eines anderen Triggers bewirken, oder wenn er eine Folge von ausgelösten Triggern erzeugt.  
  
 Geben Sie *object_id* = 0 an, um die Gesamtanzahl von Triggern in der Aufrufliste für einen bestimmten Triggertyp und eine bestimmte Ereigniskategorie zurückzugeben.  
  
 Eine TRIGGER_NESTLEVEL-Anweisung gibt 0 zurück, wenn sie außerhalb eines Triggers ausgeführt wird und ein Parameter ungleich NULL ist.  
  
 Wenn ein Parameter explizit als NULL angegeben wird, wird der Wert NULL zurückgegeben, unabhängig davon, ob TRIGGER_NESTLEVEL innerhalb oder außerhalb eines Triggers verwendet wurde.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-testing-the-nesting-level-of-a-specific-dml-trigger"></a>A. Testen der Schachtelungsebene eines bestimmten DML-Triggers  
  
```  
IF ( (SELECT TRIGGER_NESTLEVEL( OBJECT_ID('xyz') , 'AFTER' , 'DML' ) ) > 5 )  
   RAISERROR('Trigger xyz nested more than 5 levels.',16,-1)  
```  
  
### <a name="b-testing-the-nesting-level-of-a-specific-ddl-trigger"></a>B. Testen der Schachtelungsebene eines bestimmten DDL-Triggers  
  
```  
IF ( ( SELECT TRIGGER_NESTLEVEL ( ( SELECT object_id FROM sys.triggers  
WHERE name = 'abc' ), 'AFTER' , 'DDL' ) ) > 5 )  
   RAISERROR ('Trigger abc nested more than 5 levels.',16,-1)  
```  
  
### <a name="c-testing-the-nesting-level-of-all-triggers-executed"></a>C. Testen der Schachtelungsebene aller ausgeführten Trigger  
  
```  
IF ( (SELECT trigger_nestlevel() ) > 5 )  
   RAISERROR  
      ('This statement nested over 5 levels of triggers.',16,-1)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
