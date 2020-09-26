---
description: TRIGGER_NESTLEVEL (Transact-SQL)
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
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 86554070c90b2c946e79359b561da324abbf700a
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "91379535"
---
# <a name="trigger_nestlevel-transact-sql"></a>TRIGGER_NESTLEVEL (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Anzahl von Triggern zurück, die für die Anweisung ausgelöst wurden, von der der Trigger ausgeführt wurde. TRIGGER_NESTLEVEL wird in DML- und DDL-Triggern verwendet, um die aktuelle Schachtelungsebene zu bestimmen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
TRIGGER_NESTLEVEL ( [ object_id ] , [ 'trigger_type' ] , [ 'trigger_event_category' ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *object_id*  
 Die Objekt-ID eines Triggers. Wenn *object_id* angegeben wird, wird die Häufigkeit zurückgegeben, mit der der angegebene Trigger für die Anweisung ausgeführt wurde. Wenn *object_id* nicht angegeben wird, wird die Häufigkeit zurückgegeben, mit der alle Trigger für die Anweisung ausgeführt wurden.  
  
 **'** *trigger_type* **'**  
 Gibt an, ob TRIGGER_NESTLEVEL auf AFTER- oder INSTEAD OF-Trigger angewendet werden soll. Geben Sie **AFTER** für AFTER-Trigger an. Geben Sie **IOT** für INSTEAD OF-Trigger an. Wenn *trigger_type* angegeben ist, muss auch *trigger_event_category* angegeben sein.  
  
 **'** *trigger_event_category* **'**  
 Gibt an, ob TRIGGER_NESTLEVEL auf DML- oder DDL-Trigger angewendet werden soll. Geben Sie **DML** für DML-Trigger an. Geben Sie **DDL** für DDL-Trigger an. Wenn *trigger_event_category* angegeben ist, muss auch *trigger_type* angegeben sein. Beachten Sie, dass nur **AFTER** für **DDL** angegeben werden kann, weil DDL-Trigger nur AFTER-Trigger sein können.  
  
## <a name="remarks"></a>Hinweise  
 Wenn keine Parameter angegeben werden, gibt TRIGGER_NESTLEVEL die Gesamtanzahl von Triggern in der Aufrufliste zurück. Der Parameter selbst ist ebenfalls darin eingeschlossen. Es kann vorkommen, dass Parameter nicht angegeben werden, wenn ein Trigger Befehle ausführt, die das Auslösen eines anderen Triggers bewirken, oder wenn er eine Folge von ausgelösten Triggern erzeugt.  
  
 Geben Sie *object_id* = 0 an, um die Gesamtanzahl von Triggern in der Aufrufliste für einen bestimmten Triggertyp und eine bestimmte Ereigniskategorie zurückzugeben.  
  
 Eine TRIGGER_NESTLEVEL-Anweisung gibt 0 zurück, wenn sie außerhalb eines Triggers ausgeführt wird und ein Parameter ungleich NULL ist.  
  
 Wenn ein Parameter explizit als NULL angegeben wird, wird der Wert NULL zurückgegeben, unabhängig davon, ob TRIGGER_NESTLEVEL innerhalb oder außerhalb eines Triggers verwendet wurde.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-testing-the-nesting-level-of-a-specific-dml-trigger"></a>A. Testen der Schachtelungsebene eines bestimmten DML-Triggers  
  
```sql
IF ( (SELECT TRIGGER_NESTLEVEL( OBJECT_ID('xyz') , 'AFTER' , 'DML' ) ) > 5 )  
   RAISERROR('Trigger xyz nested more than 5 levels.',16,-1)  
```  
  
### <a name="b-testing-the-nesting-level-of-a-specific-ddl-trigger"></a>B. Testen der Schachtelungsebene eines bestimmten DDL-Triggers  
  
```sql
IF ( ( SELECT TRIGGER_NESTLEVEL ( ( SELECT object_id FROM sys.triggers  
WHERE name = 'abc' ), 'AFTER' , 'DDL' ) ) > 5 )  
   RAISERROR ('Trigger abc nested more than 5 levels.',16,-1)  
```  
  
### <a name="c-testing-the-nesting-level-of-all-triggers-executed"></a>C. Testen der Schachtelungsebene aller ausgeführten Trigger  
  
```sql
IF ( (SELECT trigger_nestlevel() ) > 5 )  
   RAISERROR  
      ('This statement nested over 5 levels of triggers.',16,-1)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
