---
title: TRY_PARSE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TRY_PARSE_TSQL
- TRY_PARSE
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_PARSE function
ms.assetid: 292bac1d-edd8-468c-8ff1-8c7de625bc55
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions||=azure-sqldw-latest
ms.openlocfilehash: f63e2306932250b8bac43382e4f8cffa85a0a3ed
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832827"
---
# <a name="try_parse-transact-sql"></a>TRY_PARSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-asdw-xxx-md.md)]

  Gibt das Ergebnis eines Ausdrucks zurück, das in den angeforderten Datentyp übersetzt wurde. Schlägt die Umwandlung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fehl, wird NULL zurückgegeben. Verwenden Sie TRY_PARSE nur, um eine Zeichenfolge in ein Datum und eine Uhrzeit oder in eine Zahl zu konvertieren.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TRY_PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *string_value*  
 **nvarchar**(4000)-Wert, der den formatierten Wert darstellt, der als angegebener Datentyp analysiert werden soll.  
  
 *string_value* muss eine gültige Darstellung des angeforderten Datentyps sein. Andernfalls gibt TRY_PARSE NULL zurück.  
  
 *data_type*  
 Literal, das den für das Ergebnis angeforderten Datentyp darstellt.  
  
 *culture*  
 Optionale Zeichenfolge, die die Kultur angibt, in der *string_value* formatiert wird.  
  
 Wenn das *culture* -Argument nicht angegeben wurde, wird die Sprache der aktuellen Sitzung verwendet. Diese Sprache ist entweder implizit definiert oder wird explizit mit der Anweisung SET LANGUAGE festgelegt. *culture* lässt alle von .NET Framework unterstützten Kulturen zu und ist auf die explizit durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützten Sprachen beschränkt. Wenn das *culture*-Argument nicht gültig ist, löst PARSE einen Fehler aus.  
  
## <a name="return-types"></a>Rückgabetypen  
 Gibt das Ergebnis des Ausdrucks zurück, das in den angeforderten Datentyp übersetzt wurde. Schlägt die Umwandlung fehl, wird NULL zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie TRY_PARSE nur, um eine Zeichenfolge in ein Datum und eine Uhrzeit oder in eine Zahl zu konvertieren. Für die allgemeine Typkonvertierungen sollten Sie auch weiterhin CAST oder CONVERT verwenden. Bedenken Sie, dass die Analyse des Zeichenfolgenwerts mit gewissen Leistungseinbußen verbunden ist.  
  
 Für TRY_PARSE muss .NET Framework Common Language Runtime (CLR) vorhanden sein.  
  
 Diese Funktion wird nicht remote ausgeführt, da sie die Existenz der CLR voraussetzt. Die Remoteausführung einer Funktion, die die CLR erfordert, würde einen Fehler auf dem Remoteserver auslösen.  
  
 **Weitere Informationen zum data_type-Parameter**  
  
 Die Werte für den *data_type*-Parameter sind auf die in der folgenden Tabelle dargestellten Typen sowie die zugehörigen Formate beschränkt. Die Formatinformationen werden bereitgestellt, um die Ermittlung der zulässigen Mustertypen zu unterstützen. Weitere Informationen zu Formaten finden Sie in der .NET Framework-Dokumentation für die Enumerationen **System.Globalization.NumberStyles** und **DateTimeStyles**.  
  
|Category|type|.NET-Typ|Verwendete Formate|  
|--------------|----------|---------------|-----------------|  
|Numeric|BIGINT|Int64|NumberStyles.Number|  
|Numeric|INT|Int32|NumberStyles.Number|  
|Numeric|SMALLINT|Int16|NumberStyles.Number|  
|Numeric|TINYINT|Byte|NumberStyles.Number|  
|Numeric|Decimal|Decimal|NumberStyles.Number|  
|Numeric|NUMERIC|Decimal|NumberStyles.Number|  
|Numeric|float|Double|NumberStyles.Float|  
|Numeric|real|Single|NumberStyles.Float|  
|Numeric|SMALLMONEY|Decimal|NumberStyles.Currency|  
|Numeric|money|Decimal|NumberStyles.Currency|  
|Datum und Uhrzeit|date|Datetime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Datum und Uhrzeit|time|TimeSpan|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Datum und Uhrzeit|datetime|Datetime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Datum und Uhrzeit|smalldatetime|Datetime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Datum und Uhrzeit|datetime2|Datetime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Datum und Uhrzeit|datetimeoffset|DateTimeOffset|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
  
 **Weitere Informationen zum culture-Parameter**  
  
 In der folgenden Tabelle werden die Zuordnungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sprachen zu .NET Framework-Kulturen angezeigt.  
  
|Vollständiger Name|Alias|LCID|Bestimmte Kultur|  
|---------------|-----------|----------|----------------------|  
|us_english|Englisch|1033|de-DE|  
|Deutsch|Deutsch|1031|de-DE|  
|Français|Französisch|1036|fr-FR|  
|日本語|Japanisch|1041|ja-JP|  
|Dansk|Dänisch|1030|da-DK|  
|Español|Spanisch|3082|es-ES|  
|Italiano|Italienisch|1040|it-IT|  
|Nederlands|Niederländisch|1043|nl-NL|  
|Norsk|Norwegisch|2068|nn-NO|  
|Português|Portugiesisch|2070|pt-PT|  
|Suomi|Finnisch|1035|fi-FI|  
|Svenska|Schwedisch|1053|sv-SE|  
|čeština|Tschechisch|1029|Cs-CZ|  
|magyar|Ungarisch|1038|Hu-HU|  
|polski|Polnisch|1045|Pl-PL|  
|română|Rumänisch|1048|Ro-RO|  
|hrvatski|Kroatisch|1050|hr-HR|  
|slovenčina|Slowakisch|1051|Sk-SK|  
|slovenski|Slowenisch|1060|Sl-SI|  
|ελληνικά|Griechisch|1032|El-GR|  
|български|Bulgarisch|1026|bg-BG|  
|русский|Russisch|1049|Ru-RU|  
|Türkçe|Türkisch|1\.055|Tr-TR|  
|British|Englisch (britisch)|2057|en-GB|  
|eesti|Estnisch|1061|Et-EE|  
|latviešu|Lettisch|1062|lv-LV|  
|lietuvių|Litauisch|1063|lt-LT|  
|Português (Brasil)|Brasilianisch|1046|pt-BR|  
|繁體中文|Chinesisch (traditionell)|1028|zh-TW|  
|한국어|Koreanisch|1042|Ko-KR|  
|简体中文|Chinesisch (vereinfacht)|2052|zh-CN|  
|Arabisch|Arabisch|1025|ar-SA|  
|ไทย|Thailändisch|1054|Th-TH|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-simple-example-of-try_parse"></a>A. Einfaches Beispiel für TRY_PARSE  
  
```  
SELECT TRY_PARSE('Jabberwokkie' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-detecting-nulls-with-try_parse"></a>B. Erkennen von NULL-Werten mit TRY_PARSE  
  
```  
SELECT  
    CASE WHEN TRY_PARSE('Aragorn' AS decimal USING 'sr-Latn-CS') IS NULL  
        THEN 'True'  
        ELSE 'False'  
END  
AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
True  
  
(1 row(s) affected)  
```  
  
### <a name="c-using-iif-with-try_parse-and-implicit-culture-setting"></a>C. Verwenden von IIF mit TRY_PARSE und impliziter Kultureinstellung  
  
```  
SET LANGUAGE English;  
SELECT IIF(TRY_PARSE('01/01/2011' AS datetime2) IS NULL, 'True', 'False') AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
False  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [PARSE &#40;Transact-SQL&#41;](../../t-sql/functions/parse-transact-sql.md)   
 [Konvertierungsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/conversion-functions-transact-sql.md)   
 [TRY_CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/try-convert-transact-sql.md)   
 [CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
