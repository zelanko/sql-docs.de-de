---
description: STRING_ESCAPE (Transact-SQL)
title: STRING_ESCAPE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current||>= sql-server-2016||>= sql-server-linux-2017
ms.openlocfilehash: de472b06f2d6747ced93a36f3563188e3d537d36
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461221"
---
# <a name="string_escape-transact-sql"></a>STRING_ESCAPE (Transact-SQL)


[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

Versieht Sonderzeichen in Texten mit Escapezeichen und gibt Text mit Escapezeichen zurück. **STRING_ESCAPE** ist eine deterministische Funktion, die in SQL Server 2016 eingeführt wurde. 
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
STRING_ESCAPE( text , type )  
```  

## <a name="arguments"></a>Argumente

 *text*  
 Ein **nvarchar**[expression](../../t-sql/language-elements/expressions-transact-sql.md)-Ausdruck, der das Objekt darstellt, das mit Escapezeichen versehen werden soll.  
  
 *type*  
 Versieht Regeln, die angewendet werden sollen, mit Escapezeichen. Der derzeit unterstützte Wert lautet `'json'`.  
  
## <a name="return-types"></a>Rückgabetypen

 **nvarchar(max)**-Text mit Sonder- und Steuerzeichen, die mit Escapezeichen versehen sind. Derzeit kann **STRING_ESCAPE** nur die in der folgenden Tabelle aufgeführten Sonderzeichen im JSON-Format mit Escapezeichen versehen.  
  
|Sonderzeichen|Codierte Sequenz|  
|-----------------------|----------------------|  
|Anführungszeichen (")|\\"|  
|Umgekehrter Schrägstrich (\\)| \\\\ |  
|Schrägstrich (/)|\\/|  
|Rückschritt|\b|  
|Seitenvorschub|\f|  
|Zeilenwechsel|\n|  
|Wagenrücklauf|\r|  
|Horizontaler Tabulator|\t|  
  
|Steuerzeichen|Codierte Sequenz|  
|-----------------------|----------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|...|...|  
|CHAR(31)|\u001f|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  Versehen von Text mit Escapezeichen entsprechend der JSON-Formatierungsregeln

 Über die folgende Abfrage werden Sonderzeichen unter Verwendung von JSON-Regeln mit Escapezeichen versehen und mit Escapezeichen versehener Text zurückgegeben.  
  
```sql
SELECT STRING_ESCAPE('\   /  
\\    "     ', 'json') AS escapedText;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
escapedText  
-------------------------------------------------------------  
\\\t\/\n\\\\\t\"\t
```  
  
### <a name="b-format-json-object"></a>B. Formatieren eines JSON-Objekts

 Über die folgende Abfrage wird aus Zahlen- und Zeichenfolgenvariablen JSON-Text erstellt und sämtliche Sonderzeichen im JSON-Format in Variablen mit Escapezeichen versehen.  
  
```
SET @json = FORMATMESSAGE('{ "id": %d,"name": "%s", "surname": "%s" }',
    17, STRING_ESCAPE(@name,'json'), STRING_ESCAPE(@surname,'json') );  
```  
  
## <a name="see-also"></a>Weitere Informationen

- [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
- [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
- [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
- [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
- [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
- [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
- [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
- [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
- [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
- [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/string-functions-transact-sql.md)
