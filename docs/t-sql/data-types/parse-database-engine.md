---
description: Parse (Datenbank-Engine)
title: Parse (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Parse
- Parse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Parse [Database Engine]
ms.assetid: b37e28b6-6e2e-470a-945b-ce5252da743a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8ebfca7738f8310108aab9ba988e658e7a5c1e17
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038363"
---
# <a name="parse-database-engine"></a>Parse (Datenbank-Engine)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Parse konvertiert die kanonische Zeichenfolgendarstellung einer **hierarchyid** in einen **hierarchyid**-Wert. Parse wird implizit aufgerufen, wenn eine Konvertierung von einem Zeichenfolgentyp in einen **hierarchyid**-Typ stattfindet. Dient als Gegenstück zu [ToString](../../t-sql/data-types/tostring-database-engine.md). Parse() ist eine statische Methode.
  
## <a name="syntax"></a>Syntax  
  
```sql
-- Transact-SQL syntax  
hierarchyid::Parse ( input )  
-- This is functionally equivalent to the following syntax   
-- which implicitly calls Parse():  
CAST ( input AS hierarchyid )  
```  
  
```csharp
-- CLR syntax  
static SqlHierarchyId Parse ( SqlString input )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
*input*  
[!INCLUDE[tsql](../../includes/tsql-md.md)]: Der Wert des Zeichendatentyps, der konvertiert wird.
  
CLR: Der Zeichenfolgenwert, der ausgewertet wird.
  
## <a name="return-types"></a>Rückgabetypen  
**SQL Server-Rückgabetyp: hierarchyid**
  
**CLR-Rückgabetyp: SqlHierarchyId**
  
## <a name="remarks"></a>Hinweise  
Wenn Parse einen Wert erhält, der keine gültige Zeichenfolgendarstellung einer **hierarchyid** ist, wird eine Ausnahme ausgelöst. Wenn beispielsweise **char**-Datentypen nachfolgende Leerzeichen enthalten, wird eine Ausnahme ausgelöst.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-converting-transact-sql-values-without-a-table"></a>A. Konvertieren von Transact-SQL-Werten ohne Tabelle  
Im folgenden Codebeispiel wird mithilfe von `ToString` ein **hierarchyid**-Wert in eine Zeichenfolge und mithilfe von `Parse` ein Zeichenfolgenwert in eine **hierarchyid** konvertiert.
  
```sql
DECLARE @StringValue AS NVARCHAR(4000), @hierarchyidValue AS hierarchyid  
SET @StringValue = '/1/1/3/'  
SET @hierarchyidValue = 0x5ADE  
  
SELECT hierarchyid::Parse(@StringValue) AS hierarchyidRepresentation,  
@hierarchyidValue.ToString() AS StringRepresentation ;
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
hierarchyidRepresentation    StringRepresentation
-------------------------    -----------------------
0x5ADE                       /1/1/3/
```
  
### <a name="b-clr-example"></a>B. CLR-Beispiel  
Im folgenden Codeausschnitt wird die Parse()-Methode aufgerufen:
  
```csharp
string input = "/1/2/";  
SqlHierarchyId.Parse(input);  
```  
  
## <a name="see-also"></a>Weitere Informationen
[hierarchyid-Datentyp-Methodenverweis](./hierarchyid-data-type-method-reference.md)  
[Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
