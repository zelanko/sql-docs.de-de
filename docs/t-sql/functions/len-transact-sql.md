---
title: LEN (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/03/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LEN
- LEN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- LEN function
- characters [SQL Server], number of
- number of characters
ms.assetid: fa20fee4-884d-4301-891a-c03e901345ae
caps.latest.revision: 47
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4dc46ab935360b81cd68cfce1115c21dfd33ebae
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074242"
---
# <a name="len-transact-sql"></a>LEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt die Anzahl von Zeichen im angegebenen Zeichenfolgenausdruck zurück, wobei nachfolgende Leerzeichen ausgeschlossen werden.  
  
> [!NOTE]  
>  Verwenden Sie die [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md)-Funktion, um die Anzahl von Bytes zurückzugeben, die zur Darstellung eines Ausdrucks verwendet werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
LEN ( string_expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *string_expression*  
 Ist der auszuwertende [Zeichenfolgenausdruck](../../t-sql/language-elements/expressions-transact-sql.md). *string_expression* kann eine Konstante, Variable oder Spalte mit Zeichen- oder Binärdaten darstellen.  
  
## <a name="return-types"></a>Rückgabetypen  
 **bigint**, wenn *expression* vom Datentyp **varchar(max)**, **nvarchar(max)** oder **varbinary(max)** ist; andernfalls **int**.  
  
 Wenn Sie SC-Sortierungen verwenden, betrachtet der zurückgegebene ganzzahlige Wert UTF-16-Ersatzpaare als einzelne Zeichen. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="remarks"></a>Remarks  
 Durch LEN werden nachfolgende Leerräume ausgeschlossen. Wenn dies ein Problem darstellt, erwägen Sie die Verwendung der Funktion [DATALENGTH &#40;Transact-SQL&#41;](../../t-sql/functions/datalength-transact-sql.md), die die Zeichenfolge nicht abtrennt. Wenn eine Unicode-Zeichenfolge verarbeitet wird, gibt DATALENGTH die doppelte Anzahl von Zeichen zurück. Im folgenden Beispiel werden LEN und DATALENGTH mit nachfolgenden Leerräumen veranschaulicht.  
  
```  
DECLARE @v1 varchar(40),  
    @v2 nvarchar(40);  
SELECT   
@v1 = 'Test of 22 characters ',   
@v2 = 'Test of 22 characters ';  
SELECT LEN(@v1) AS [varchar LEN] , DATALENGTH(@v1) AS [varchar DATALENGTH];  
SELECT LEN(@v2) AS [nvarchar LEN], DATALENGTH(@v2) AS [nvarchar DATALENGTH];  
  
```  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel wählt die Anzahl von Zeichen und die Daten in `FirstName` für Personen in `Australia` aus. In diesem Beispiel wird die AdventureWorks-Datenbank verwendet.  
  
```  
SELECT LEN(FirstName) AS Length, FirstName, LastName   
FROM Sales.vIndividualCustomer  
WHERE CountryRegionName = 'Australia';  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 Im folgenden Beispiel wird die Anzahl von Zeichen in der Spalte `FirstName` zurückgegeben, und die Vor- und Nachnamen der Mitarbeiter werden in `Australia` zurückgegeben.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT LEN(FirstName) AS FNameLength, FirstName, LastName   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.DimGeography AS g   
    ON e.SalesTerritoryKey = g.SalesTerritoryKey   
WHERE EnglishCountryRegionName = 'Australia';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FNameLength  FirstName  LastName  
-----------  ---------  ---------------  
4            Lynn       Tsoflias
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [DATALENGTH &#40;Transact-SQL&#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [CHARINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/charindex-transact-sql.md)  
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)  
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)   
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/string-functions-transact-sql.md)   
  
  


