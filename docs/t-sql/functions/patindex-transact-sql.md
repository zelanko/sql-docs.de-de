---
description: PATINDEX (Transact-SQL)
title: PATINDEX (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/19/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PATINDEX
- PATINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- first occurrence of pattern [SQL Server]
- searches [SQL Server], pattern starting position
- starting position of patten search
- pattern searching [SQL Server]
- PATINDEX function
ms.assetid: c0dfb17f-2230-4e36-98da-a9b630bab656
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c4d2ee21a4b2c2975fcead1e883cb28459c608dd
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88363376"
---
# <a name="patindex-transact-sql"></a>PATINDEX (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt für alle gültigen Text- und Zeichendatentypen die Startposition des ersten Auftretens eines Musters in einem angegebenen Ausdruck zurück bzw. 0, wenn das Muster nicht gefunden wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
PATINDEX ( '%pattern%' , expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *pattern*  
 Ein Zeichenausdruck, der die zu suchende Sequenz enthält. Platzhalterzeichen können verwendet werden, jedoch muss das %-Zeichen vorangestellt werden und *pattern* folgen (es sei denn, Sie suchen nach den ersten oder letzten Zeichen). *pattern* ist ein Ausdruck aus der Kategorie der Zeichenfolgen-Datentypen. *pattern* ist auf 8000 Zeichen beschränkt.

 > [!NOTE]
 > Obwohl reguläre Ausdrücke in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht nativ unterstützt werden, kann ein ähnlich komplexer Musterabgleich durch Verwendung unterschiedlicher Platzhalterausdrücke erzielt werden. In der Dokumentation zum [Zeichenfolgenoperator](../../t-sql/language-elements/string-operators-transact-sql.md) finden Sie weitere Details zur Platzhaltersyntax.
  
 *expression*  
 Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md), in der Regel eine Spalte, der nach dem angegebenen Muster durchsucht wird. *expression* ist ein Ausdruck aus der Kategorie der Zeichenfolgen-Datentypen.  
  
## <a name="return-types"></a>Rückgabetypen  
**bigint**, wenn *expression* vom Datentyp **varchar(max)** oder **nvarchar(max)** ist; andernfalls **int**.  
  
## <a name="remarks"></a>Hinweise  
Wenn *pattern* oder *expression* NULL ist, gibt PATINDEX NULL zurück.  
 
Die Startposition für PATINDEX ist 1.
 
PATINDEX führt Vergleiche auf Basis der Sortierung der Eingabe aus. Zum Ausführen eines Vergleichs in einer angegebenen Sortierung können Sie mithilfe von COLLATE eine ausdrückliche Sortierung auf die Eingabe anwenden.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Ergänzende Zeichen (Ersatzpaare)  
Bei SC-Sortierungen werden UTF-16-Ersatzpaare im *expression*-Parameter vom Rückgabewert als einzelnes Zeichen gezählt. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
0x0000 (**char(0)**) ist ein nicht definiertes Zeichen in Windows-Sortierungen und kann nicht in PATINDEX enthalten sein.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-simple-patindex-example"></a>A. Ein einfaches Beispiel für PATINDEX  
 Im folgenden Beispiel wird eine kurze Zeichenfolge (`interesting data`) auf die Startposition der Zeichen `ter` überprüft.  
  
```sql  
SELECT position = PATINDEX('%ter%', 'interesting data');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

```
position
--------
3
```
  
### <a name="b-using-a-pattern-with-patindex"></a>B. Verwenden eines Musters mit PATINDEX  
Im folgenden Beispiel wird die Position gefunden, an der in einer bestimmten Zeile der `ensure`-Spalte in der `DocumentSummary`-Tabelle der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank das Muster `Document` beginnt.  
  
```sql  
SELECT position = PATINDEX('%ensure%',DocumentSummary)  
FROM Production.Document  
WHERE DocumentNode = 0x7B40;  
GO   
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
position
--------  
64  
```  
  
Wenn Sie die zu durchsuchenden Zeilen nicht durch eine `WHERE`-Klausel beschränken, gibt die Abfrage alle Zeilen in der Tabelle zurück und meldet Werte ungleich 0 für die Zeilen, in denen das Muster gefunden wurde, sowie 0 für alle Zeilen, in denen das Muster nicht gefunden wurde.  
  
### <a name="c-using-wildcard-characters-with-patindex"></a>C. Verwenden von Platzhalterzeichen mit PATINDEX  
 Im folgenden Beispiel wird mit dem Platzhalterzeichen % und dem Platzhalterzeichen _ nach der Position gesucht, an der das Muster `'en'` in der angegebenen Zeichenfolge beginnt und auf das ein beliebiges Zeichen sowie `'ure'` folgen (Index beginnt bei 1):  
  
```sql  
SELECT position = PATINDEX('%en_ure%', 'Please ensure the door is locked!');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
position
--------  
8  
```  
  
`PATINDEX` funktioniert analog zu `LIKE`; Sie können daher eines der Platzhalterzeichen verwenden. Sie müssen das Muster nicht mit Prozentzeichen umschließen. `PATINDEX('a%', 'abc')` gibt 1 und `PATINDEX('%a', 'cba')` 3 zurück.  
  
 Im Gegensatz zu `LIKE` gibt `PATINDEX` ähnlich wie `CHARINDEX` eine Position zurück.  

### <a name="d-using-complex-wildcard-expressions-with-patindex"></a>D: Verwenden komplexer Platzhalterausdrücke mit PATINDEX 
Im folgenden Beispiel wird der  [Zeichenfolgenoperator](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)`[^]` verwendet, um die Position eines Zeichens zu finden, das keine Zahl, kein Buchstabe oder kein Leerzeichen ist.

```sql
SELECT position = PATINDEX('%[^ 0-9A-z]%', 'Please ensure the door is locked!'); 
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

```
position
--------
33
```

### <a name="e-using-collate-with-patindex"></a>E. Verwenden von COLLATE mit PATINDEX  
 Im folgenden Beispiel wird die `COLLATE`-Funktion verwendet, um die Sortierung des durchsuchten Ausdrucks ausdrücklich anzugeben.  
  
```sql  
USE tempdb;  
GO  
SELECT PATINDEX ( '%ein%', 'Das ist ein Test'  COLLATE Latin1_General_BIN) ;  
GO  
```  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

```
position
--------
9
```

### <a name="f-using-a-variable-to-specify-the-pattern"></a>F. Verwenden einer Variable, um das Muster anzugeben  
Im folgenden Beispiel wird eine Variable verwendet, um einen Wert an den *pattern*-Parameter zu übergeben. In diesem Beispiel wird die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank verwendet.  
  
```sql  
DECLARE @MyValue VARCHAR(10) = 'safety';   
SELECT position = PATINDEX('%' + @MyValue + '%', DocumentSummary)   
FROM Production.Document  
WHERE DocumentNode = 0x7B40;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
position
--------  
22
```  
  
## <a name="see-also"></a>Siehe auch  
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [CHARINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/charindex-transact-sql.md)  
 [LEN &#40;Transact-SQL&#41;](../../t-sql/functions/len-transact-sql.md)  
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen (Transact-SQL))](../../t-sql/functions/string-functions-transact-sql.md)   
 [&#40;Wildcard - Character&#40;s&#41; to Match&#41; &#40;Transact-SQL&#41; (% (Platzhalterzeichen – zu suchende(s) Zeichen) (Transact-SQL))](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [&#40;Wildcard - Character&#40;s&#41; to Match&#41; &#40;Transact-SQL&#41; (% (Platzhalterzeichen – nicht zu suchende(s) Zeichen) (Transact-SQL))](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)   
 [_ &#40;Wildcard - Match One Character&#41; &#40;Transact-SQL&#41; (_ (Platzhalterzeichen – einzelnes zu suchendes Zeichen) (Transact-SQL))](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)   
 [Percent character &#40;Wildcard - Character&#40;s&#41; to Match&#41; &#40;Transact-SQL&#41; (Prozentzeichen (Platzhalterzeichen – zu suchende(s) Zeichen) (Transact-SQL))](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)  
  
  


