---
description: IDENT_CURRENT (Transact-SQL)
title: IDENT_CURRENT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IDENT_CURRENT
- IDENT_CURRENT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- last identity value generated for table
- identity values [SQL Server], last generated
- identity columns, current value
- IDENT_CURRENT function
ms.assetid: 21517ced-39f5-4cd8-8d9c-0a0b8aff554a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7fffc7d4a09e29066942c321fc65b48202d247ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88365476"
---
# <a name="ident_current-transact-sql"></a>IDENT_CURRENT (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt den letzten für eine angegebene Tabelle oder Sicht generierten Identitätswert zurück. Der letzte generierte Identitätswert kann sich auf eine beliebige Sitzung und einen beliebigen Gültigkeitsbereich beziehen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
IDENT_CURRENT( 'table_or_view' )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
*table_or_view*  
Der Name der Tabelle oder Ansicht, deren Identitätswert zurückgegeben wird. *table_or_view* ist vom Datentyp **varchar** und hat keinen Standardwert.  
  
## <a name="return-types"></a>Rückgabetypen  
**numeric**([@@MAXPRECISION](../../t-sql/functions/max-precision-transact-sql.md),0))  
  
## <a name="exceptions"></a>Ausnahmen  
Gibt NULL bei einem Fehler zurück oder wenn ein Aufrufer nicht über Berechtigungen zum Anzeigen des Objekts verfügt.  
  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann ein Benutzer nur die Metadaten sicherungsfähiger Elemente anzeigen, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Dies bedeutet, dass Metadaten ausgebende integrierte Funktionen, z. B. IDENT_INCR, möglicherweise NULL zurückgeben, wenn dem Benutzer für das Objekt keine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Hinweise  
IDENT_CURRENT ähnelt den [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-Identitätsfunktionen SCOPE_IDENTITY und @@IDENTITY. Alle drei Funktionen geben die zuletzt generierten Identitätswerte zurück. Der Gültigkeitsbereich und die Sitzung, für die *last* definiert ist, unterscheiden sich jedoch bei jeder dieser drei Funktionen:  

-   IDENT_CURRENT gibt den letzten für eine bestimmte Tabelle in einer Sitzung oder einem Gültigkeitsbereich generierten Identitätswert zurück.  
-   @@IDENTITY gibt den letzten Identitätswert zurück, der für eine Tabelle in der aktuellen Sitzung in allen Gültigkeitsbereichen generiert wurde.  
-   SCOPE_IDENTITY gibt den letzten Identitätswert zurück, der für eine Tabelle in der aktuellen Sitzung im aktuellen Gültigkeitsbereich generiert wurde.  
  
Wenn der IDENT_CURRENT-Wert NULL ist (da die Tabelle keine Zeilen enthielt oder abgeschnitten wurde), gibt die IDENT_CURRENT-Funktion den Ausgangswert zurück.  
  
Fehlgeschlagene Anweisungen oder Transaktionen können die aktuelle Identität für eine Tabelle ändern und zu Lücken in den Identitätsspaltenwerten führen. Für den Identitätswert erfolgt kein Rollback, auch wenn für die Transaktion, die versuchte, den Wert in die Tabelle einzufügen, kein Commit ausgeführt wird. Wenn beispielsweise eine INSERT-Anweisung aufgrund einer IGNORE_DUP_KEY-Verletzung fehlschlägt, wird der aktuelle Identitätswert für die Tabelle trotzdem inkrementiert.  

Wenn Sie IDENT_CURRENT für eine Ansicht verwenden, die Verknüpfungen enthält, wird NULL zurückgegeben. Dies ist unabhängig davon, ob nur eine oder mehrere verbundene Tabellen über eine Identitätsspalte verfügen. 
  
> [!IMPORTANT]
> IDENT_CURRENT ist nur bedingt geeignet, um den nächsten generierten Identitätswert vorherzusagen. Der tatsächlich generierte Wert kann sich aufgrund von Einfügungen durch andere Sitzungen von IDENT_CURRENT plus IDENT_INCR unterscheiden.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-last-identity-value-generated-for-a-specified-table"></a>A. Zurückgeben des letzten für eine angegebene Tabelle generierten Identitätswertes  
 Im folgenden Beispiel wird der letzte Identitätswert zurückgegeben, der für die `Person.Address`-Tabelle in der `AdventureWorks2012`-Datenbank generiert wurde.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT IDENT_CURRENT ('Person.Address') AS Current_Identity;  
GO  
```  
  
### <a name="b-comparing-identity-values-returned-by-ident_current-identity-and-scope_identity"></a>B. Vergleichen der von IDENT_CURRENT, @@IDENTITY und SCOPE_IDENTITY zurückgegebenen Identitätswerte  
 Das folgende Beispiel zeigt verschiedene Identitätswerte, die von `IDENT_CURRENT`, `@@IDENTITY` und `SCOPE_IDENTITY` zurückgegeben werden.  
  
```sql 
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N't6', N'U') IS NOT NULL   
    DROP TABLE t6;  
GO  
IF OBJECT_ID(N't7', N'U') IS NOT NULL   
    DROP TABLE t7;  
GO  
CREATE TABLE t6(id int IDENTITY);  
CREATE TABLE t7(id int IDENTITY(100,1));  
GO  
CREATE TRIGGER t6ins ON t6 FOR INSERT   
AS  
BEGIN  
   INSERT t7 DEFAULT VALUES  
END;  
GO  
--End of trigger definition  
  
SELECT id FROM t6;  
--IDs empty.  
  
SELECT id FROM t7;  
--ID is empty.  
  
--Do the following in Session 1  
INSERT t6 DEFAULT VALUES;  
SELECT @@IDENTITY;  
/*Returns the value 100. This was inserted by the trigger.*/  
  
SELECT SCOPE_IDENTITY();  
/* Returns the value 1. This was inserted by the   
INSERT statement two statements before this query.*/  
  
SELECT IDENT_CURRENT('t7');  
/* Returns value inserted into t7, that is in the trigger.*/  
  
SELECT IDENT_CURRENT('t6');  
/* Returns value inserted into t6. This was the INSERT statement four statements before this query.*/  
  
-- Do the following in Session 2.  
SELECT @@IDENTITY;  
/* Returns NULL because there has been no INSERT action   
up to this point in this session.*/  
  
SELECT SCOPE_IDENTITY();  
/* Returns NULL because there has been no INSERT action   
up to this point in this scope in this session.*/  
  
SELECT IDENT_CURRENT('t7');  
/* Returns the last value inserted into t7.*/  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [@@IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/identity-transact-sql.md)   
 [SCOPE_IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [IDENT_INCR &#40;Transact-SQL&#41;](../../t-sql/functions/ident-incr-transact-sql.md)   
 [IDENT_SEED &#40;Transact-SQL&#41;](../../t-sql/functions/ident-seed-transact-sql.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
