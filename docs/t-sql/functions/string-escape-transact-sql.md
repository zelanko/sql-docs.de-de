---
title: STRING_ESCAPE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 75eaf0510fc4c897d6ecb473660a71bf31842e7a
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37789431"
---
# <a name="stringescape-transact-sql"></a>STRING_ESCAPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Versieht Sonderzeichen in Texten mit Escapezeichen und gibt Text mit Escapezeichen zurück. **STRING_ESCAPE** ist eine deterministische Funktion.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|Umgekehrter Schrägstrich (\\)|\\\|  
|Schrägstrich (/)|\\/|  
|Rücktaste|\b|  
|Seitenvorschub|\f|  
|Neue Zeile|\n|  
|Wagenrücklauf|\r|  
|Horizontaler Tabstopp|\t|  
  
|Steuerzeichen|Codierte Sequenz|  
|-----------------------|----------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|...|...|  
|CHAR(31)|\u001f|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  Versehen von Text mit Escapezeichen entsprechend der JSON-Formatierungsregeln  
 Über die folgende Abfrage werden Sonderzeichen unter Verwendung von JSON-Regeln mit Escapezeichen versehen und mit Escapezeichen versehener Text zurückgegeben.  
  
```  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen (Transact-SQL))](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
