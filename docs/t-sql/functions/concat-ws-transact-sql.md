---
title: CONCAT_WS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- CONCAT_WS
- CONCAT_WS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_WS function
ms.assetid: f1375fd7-a2fd-48bf-922a-4f778f0deb1f
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fcdbb300bbc9209f284cd5a92d192a219f79052d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075328"
---
# <a name="concatws-transact-sql"></a>CONCAT_WS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-asdw-xxx-md.md)]

Diese Funktion gibt eine Zeichenfolge zurück, die das Ergebnis einer End-to-End-Verkettung oder -Verknüpfung von mindestens zwei Zeichenfolgenwerten darstellt. Sie trennt diese verketteten Zeichenfolgenwerte mit dem im ersten Funktionsargument angegebenen Trennzeichen. (`CONCAT_WS` gibt die Anweisung *concatenate with separator* (mit Trennzeichen verketten) an.)

##  <a name="syntax"></a>Syntax   
```sql
CONCAT_WS ( separator, argument1, argument2 [, argumentN]... )
```

## <a name="arguments"></a>Argumente   
Trennzeichen  
Ein Ausdruck beliebigen Typs (`char`, `nchar`, `nvarchar` oder `varchar`).

argument1, argument2, argument*N*  
Ein Ausdruck beliebigen Typs.

## <a name="return-types"></a>Rückgabetypen
Ein Zeichenfolgenwert, dessen Länge und Typ von der Eingabe abhängig sind.

## <a name="remarks"></a>Remarks   
`CONCAT_WS` lässt eine variable Anzahl von Zeichenfolgenargumenten zu und verkettet (oder verknüpft) sie in einer einzelnen Zeichenfolge. Sie trennt diese verketteten Zeichenfolgenwerte mit dem im ersten Funktionsargument angegebenen Trennzeichen. `CONCAT_WS` erfordert ein Trennzeichen und mindestens zwei weitere Zeichenfolgenwerte als Argumente, andernfalls gibt `CONCAT_WS` einen Fehler aus. Alle Argumente werden von `CONCAT_WS` vor der Verkettung implizit in Zeichenfolgentypen konvertiert. 

Die implizite Konvertierung in Zeichenfolgen erfolgt basierend auf den vorhandenen Regeln für Datentypkonvertierungen. Weitere Informationen zu Verhaltens- und Datentypkonvertierungen finden Sie unter [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md).

### <a name="treatment-of-null-values"></a>Behandeln von NULL-Werten

`CONCAT_WS` ignoriert die `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}`-Einstellung.

Wenn `CONCAT_WS` Argumente nur mit NULL-Werten empfängt, wird eine leere Zeichenfolge vom Typ varchar(1) zurückgegeben.

`CONCAT_WS` ignoriert NULL-Werte bei der Verkettung und fügt keine Trennzeichen zwischen NULL-Werten hinzu. Daher kann `CONCAT_WS` die Verkettung von Zeichenfolgen, in denen möglicherweise „leere“ Werte auftreten, wie etwa ein zweites Adressfeld, sauber verarbeiten. Weitere Informationen finden Sie unter Beispiel B.

Wenn ein Szenario durch ein Trennzeichen getrennte NULL-Werte beinhaltet, ziehen Sie die Funktion `ISNULL` in Erwägung. Weitere Informationen finden Sie unter Beispiel C.

## <a name="examples"></a>Beispiele   

### <a name="a--concatenating-values-with-separator"></a>A.  Verketten von Werten mit einem Trennzeichen
Dieses Beispiel verkettet drei Spalten der sys.databases-Tabelle, wobei die Werte durch das Trennzeichen `-` voneinander getrennt werden.   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1 - SIMPLE - NONE |
|2 - SIMPLE - NONE |
|3 - FULL - NONE |
|4 - SIMPLE - NONE |


### <a name="b--skipping-null-values"></a>B.  Überspringen von NULL-Werten
In diesem Beispiel werden `NULL`-Werte in der Argumentliste ignoriert.

```sql
SELECT CONCAT_WS(',','1 Microsoft Way', NULL, NULL, 'Redmond', 'WA', 98052) AS Address;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
Address
------------   
1 Microsoft Way,Redmond,WA,98052
```

### <a name="c--generating-csv-file-from-table"></a>C.  Generieren einer CSV-Datei aus einer Tabelle
Dieses Beispiel verwendet ein Komma `,` als Trennzeichen und fügt ein Wagenrücklaufzeichen `char(13)` hinzu, sodass ein durch Kommas getrenntes Werteformat im Resultset entsteht.

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, recovery_model_desc, containment_desc), char(13)) AS DatabaseInfo
FROM sys.databases
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
DatabaseInfo
------------   
1,SIMPLE,NONE
2,SIMPLE,NONE
3,FULL,NONE 
4,SIMPLE,NONE 
```

CONCAT_WS ignoriert NULL-Werte in den Spalten. Umschließen Sie eine Spalte, die NULL-Werte zulässt, mit der `ISNULL`-Funktion, und geben Sie einen Standardwert an. Weitere Informationen finden Sie in diesem Beispiel:

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, ISNULL(recovery_model_desc,''), ISNULL(containment_desc,'N/A')), char(13)) AS DatabaseInfo
FROM sys.databases;
```

## <a name="see-also"></a>Siehe auch
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen (Transact-SQL))](../../t-sql/functions/string-functions-transact-sql.md)  

