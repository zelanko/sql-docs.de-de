---
title: DROP TYPE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP TYPE
- DROP_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [SQL Server], deleting
- UDTs [SQL Server], deleting
- alias data types [SQL Server], removing
- DROP TYPE statement
ms.assetid: 11bf83f9-0718-4238-a835-83d2eb14ae7b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b6416febd415ef75f2455a55c14c2e220c4b5b0a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62681512"
---
# <a name="drop-type-transact-sql"></a>DROP TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Entfernt einen Aliasdatentyp oder einen benutzerdefinierten CLR-Typ (Common Language Runtime) aus der aktuellen Datenbank.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
DROP TYPE [ IF EXISTS ] [ schema_name. ] type_name [ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 *IF EXISTS*  
 **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis zur [aktuellen Version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Löscht den Typ nur, wenn dieser bereits vorhanden ist.  
  
 *schema_name*  
 Der Name des Schemas, zu dem der Aliastyp oder benutzerdefinierte Typ gehört.  
  
 *type_name*  
 Der Name des Aliasdatentyps oder benutzerdefinierten Typs, den Sie löschen möchten.  
  
## <a name="remarks"></a>Remarks  
 Die DROP TYPE-Anweisung wird nicht ausgeführt, wenn eine der folgenden Bedingungen zutrifft:  
  
-   In der Datenbank sind Tabellen vorhanden, die Spalten des Aliasdatentyps oder benutzerdefinierten Typs enthalten. Informationen zu Spalten mit Aliastypen oder benutzerdefinierten Typen erhalten Sie, indem Sie die Katalogsichten [sys.columns](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) oder [sys.column_type_usages](../../relational-databases/system-catalog-views/sys-column-type-usages-transact-sql.md) abfragen.  
  
-   Es sind berechnete Spalten, CHECK-Einschränkungen, schemagebundene Sichten und schemagebundene Funktionen enthalten, deren Definitionen auf den Aliastyp oder benutzerdefinierten Typ verweisen. Informationen zu diesen Verweisen erhalten Sie, indem Sie die [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)-Katalogsicht abfragen.  
  
-   Es sind in der Datenbank erstellte Funktionen, gespeicherte Prozeduren oder Trigger vorhanden, die Variablen und Parameter des Aliastyps oder benutzerdefinierten Typs verwenden. Informationen zu Parametern mit Aliastypen oder benutzerdefinierten Typen erhalten Sie, indem Sie die Katalogsichten [sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md) oder [sys.parameter_type_usages](../../relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql.md) abfragen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert entweder die CONTROL-Berechtigung für *type_name* oder die ALTER-Berechtigung für *schema_name*.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird davon ausgegangen, dass ein Typ namens `ssn` bereits in der aktuellen Datenbank erstellt wurde.  
  
```  
DROP TYPE ssn ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
