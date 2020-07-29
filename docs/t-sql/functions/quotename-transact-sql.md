---
title: QUOTENAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- QUOTENAME_TSQL
- QUOTENAME
dev_langs:
- TSQL
helpviewer_keywords:
- delimited identifiers [SQL Server]
- input strings [SQL Server]
- Unicode [SQL Server], delimited identifiers
- QUOTENAME function
- valid identifiers [SQL Server]
ms.assetid: 34d47f1e-2ac7-4890-8c9c-5f60f115e076
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 21f3e3ee374403b92c984f3914a76e5ecf95a4ca
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87111398"
---
# <a name="quotename-transact-sql"></a>QUOTENAME (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt eine Unicode-Zeichenfolge mit hinzugefügten Trennzeichen zurück, sodass die Eingabezeichenfolge ein gültiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Begrenzungsbezeichner wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql
QUOTENAME ( 'character_string' [ , 'quote_character' ] )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 '*character_string*'  
 Eine Zeichenfolge von Unicode-Zeichendaten. *character_string* ist vom Datentyp **sysname** und auf 128 Zeichen beschränkt. Eingaben, die größer als 128 Zeichen sind, geben NULL zurück.  
  
 '*quote_character*'  
 Eine Zeichenfolge mit einem Zeichen, das als Trennzeichen verwendet wird. Dies kann ein einfaches Anführungszeichen ( **'** ) sein, eine linke oder recht eckige Klammer ( **[]** ), ein doppeltes Anführungszeichen ( **"** ), eine linke oder recht runde Klammer ( **()** ), ein größer als- oder kleiner als-Zeichen ( **><** ), eine linke oder rechte geschweifte Klammer ( **{}** ) oder ein Hochkomma/Backtick ( **\`** ). NULL wird zurückgegeben, wenn ein unzulässiges Zeichen angegeben wird. Wenn *quote_character* nicht angegeben wird, werden eckige Klammern verwendet.  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar(258)**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mit der Zeichenfolge `abc[]def` und den Zeichen `[` und `]` ein gültiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Begrenzungsbezeichner erstellt.  
  
```sql
SELECT QUOTENAME('abc[]def');
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc[]]def]
  
(1 row(s) affected)  
```  
  
 Beachten Sie, dass die rechte Klammer in der Zeichenfolge `abc[]def` verdoppelt wurde, um ein Escapezeichen anzugeben.  
 
 Im folgenden Beispiel wird eine Zeichenfolge in Anführungszeichen zum Benennen einer Spalte vorbereitet.  
  
```sql
DECLARE @columnName NVARCHAR(255)='user''s "custom" name'
DECLARE @sql NVARCHAR(MAX) = 'SELECT FirstName AS ' + QUOTENAME(@columnName) + ' FROM dbo.DimCustomer'

EXEC sp_executesql @sql
```
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird mit der Zeichenfolge `abc def` und den Zeichen `[` und `]` ein gültiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Begrenzungsbezeichner erstellt.  
  
```sql
SELECT QUOTENAME('abc def');   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc def]  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [PARSENAME &#40;Transact-SQL&#41;](../../t-sql/functions/parsename-transact-sql.md)  
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/string-functions-transact-sql.md)  
