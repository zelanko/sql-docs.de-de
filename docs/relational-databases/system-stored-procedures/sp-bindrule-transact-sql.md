---
title: sp_bindrule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindrule_TSQL
- sp_bindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindrule
ms.assetid: 2606073e-c52f-498d-a923-5026b9d97e67
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c89b2cb803df80872d82f18b5f26b207e9e4bc38
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828479"
---
# <a name="sp_bindrule-transact-sql"></a>sp_bindrule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Bindet eine Regel an eine Spalte oder an einen Aliasdatentyp.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Verwenden[Sie stattdessen UNIQUE-Einschränkungen und Check-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md) . Check-Einschränkungen werden mit dem Check-Schlüsselwort der Anweisungen [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) oder [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) erstellt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_bindrule [ @rulename = ] 'rule' ,   
     [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @rulename = ] 'rule'`Der Name einer Regel, die von der CREATE RULE-Anweisung erstellt wurde. die *Regel* ist vom Datentyp **nvarchar (776)** und hat keinen Standardwert.  
  
`[ @objname = ] 'object_name'`Die Tabelle und Spalte oder der Alias Datentyp, an den die Regel gebunden werden soll. Eine Regel kann nicht an die Datentypen **text**, **ntext**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, einen CLR-benutzerdefinierten Typ oder an **timestamp**-Spalten gebunden werden. An eine berechnete Spalte kann keine Regel gebunden werden.  
  
 *object_name* ist vom Datentyp **nvarchar (776)** und hat keinen Standardwert. Wenn *object_name* ein einteilige Name ist, wird er als Alias Datentyp aufgelöst. Ein zwei- oder dreiteiliger Name wird zunächst als Tabelle und Spalte aufgelöst. Wenn die Auflösung fehlschlägt, wird er als Aliasdatentyp aufgelöst. Standardmäßig erben vorhandene Spalten des Alias Datentyps die *Regel* , es sei denn, eine Regel wurde direkt an die Spalte gebunden.  
  
> [!NOTE]  
>  *object_name* können die Klammer Zeichen **[** und **]** als Begrenzungs Bezeichner enthalten. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
> [!NOTE]  
>  Regeln, die für Ausdrücke erstellt werden, die Aliasdatentypen verwenden, können an Spalten oder Aliasdatentypen gebunden werden. Wenn darauf verwiesen wird, schlägt jedoch die Kompilierung fehl. Vermeiden Sie die Verwendung von Regeln, die für Aliasdatentypen erstellt wurden.  
  
`[ @futureonly = ] 'futureonly_flag'`Wird nur beim Binden einer Regel an einen Alias Datentyp verwendet. *future_only_flag* ist vom Datentyp **varchar (15)** und hat den Standardwert NULL. Wenn dieser Parameter auf **futureonly** festgelegt ist, wird verhindert, dass vorhandene Spalten eines Alias Datentyps die neue Regel erben. Wenn *futureonly_flag* NULL ist, wird die neue Regel an alle Spalten des Alias Datentyps gebunden, die derzeit keine Regel haben oder die die vorhandene Regel des Alias Datentyps verwenden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können eine neue Regel an eine Spalte binden (obwohl eine Check-Einschränkung bevorzugt wird) oder an einen Alias Datentyp mit **sp_bindrule** , ohne die Bindung für eine vorhandene Regel aufzuheben. Die alte Regel wird überschrieben. Wenn eine Regel an eine Spalte gebunden wird, für die eine CHECK-Einschränkung vorhanden ist, werden alle Einschränkungen ausgewertet. Das Binden einer Regel an einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp ist nicht möglich.  
  
 Die Regel tritt in Kraft, wenn eine INSERT-Anweisung ausgeführt wird, nicht aber beim Binden. Sie können eine Zeichen Regel an eine Spalte des **numerischen** Datentyps binden, obwohl ein solcher Einfügevorgang ungültig ist.  
  
 Vorhandene Spalten des Alias Datentyps erben die neue Regel, es sei denn, *futureonly_flag* als **futureonly**angegeben. Neue Spalten, die mit dem Aliasdatentyp definiert sind, erben immer die Regel. Wenn jedoch die ALTER COLUMN-Klausel einer ALTER TABLE-Anweisung den Datentyp einer Spalte in einen Aliasdatentyp ändert, der an eine Regel gebunden ist, wird diese Regel nicht an die Spalte vererbt. Die Regel muss mithilfe **sp_bindrule**an die Spalte gebunden werden.  
  
 Wenn Sie eine Regel an eine Spalte binden, werden der Tabelle **sys. Columns** zugehörige Informationen hinzugefügt. Wenn Sie eine Regel an einen Alias Datentyp binden, werden der Tabelle **sys. types** zugehörige Informationen hinzugefügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Um eine Regel an eine Tabellenspalte zu binden, benötigen Sie die ALTER-Berechtigung für die Tabelle. Um eine Regel an einen Aliasdatentyp zu binden, benötigen Sie die CONTROL-Berechtigung für den Aliasdatentyp oder die ALTER-Berechtigung für das Schema, dem der Typ angehört.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-binding-a-rule-to-a-column"></a>A. Binden einer Regel an eine Spalte  
 Unter der Annahme, dass in der aktuellen Datenbank eine Regel mit dem Namen `today` mit der CREATE RULE-Anweisung erstellt wurde, wird in diesem Beispiel diese Regel an die Spalte `HireDate` der Tabelle `Employee` gebunden. Wird der Tabelle `Employee` eine Zeile hinzugefügt, werden die Daten für die Spalte `HireDate` in Hinblick auf die Regel `today` überprüft.  
  
```  
USE master;  
GO  
EXEC sp_bindrule 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-rule-to-an-alias-data-type"></a>B. Binden einer Regel an einen Aliasdatentyp  
 Unter der Annahme, eine Regel namens `rule_ssn` und ein Aliasdatentyp namens `ssn` sind vorhanden, wird in diesem Beispiel `rule_ssn` an `ssn` gebunden. Alle Spalten vom Datentyp `ssn` erben in einer CREATE TABLE-Anweisung die Regel `rule_ssn`. Vorhandene Spalten vom Typ `ssn` Erben auch die `rule_ssn` Regel, sofern nicht **futureonly** für *futureonly_flag*angegeben ist oder `ssn` eine Regel direkt an Sie gebunden ist. An Spalten gebundene Regeln haben immer Vorrang vor den an Datentypen gebundenen Regeln.  
  
```  
USE master;  
GO  
EXEC sp_bindrule 'rule_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonly_flag"></a>C. Verwenden des futureonly_flag  
 Im folgenden Beispiel wird die Regel `rule_ssn` an den Aliasdatentyp `ssn` gebunden. Da `futureonly` angegeben wurde, sind keine vorhandenen Spalten des Typs `ssn` betroffen.  
  
```  
USE master;  
GO  
EXEC sp_bindrule rule_ssn, 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D: Verwenden von Begrenzungs Bezeichnerzeichen  
 Das folgende Beispiel zeigt die Verwendung von Begrenzungs bezeichnerbezeichnerbezeichnerzeichen in *object_name* -Parametern.  
  
```  
USE master;  
GO  
CREATE TABLE [t.2] (c1 int) ;  
-- Notice the period as part of the table name.  
EXEC sp_bindrule rule1, '[t.2].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [Drop Rule &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_unbindrule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
