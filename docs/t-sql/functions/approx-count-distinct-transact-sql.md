---
title: APPROX_COUNT_DISTINCT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/23/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- APPROX_COUNT_DISTINCT
dev_langs:
- TSQL
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5b0eb2db49a4bda6fc8be884790c3caf9cfdb7bd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836724"
---
# <a name="approxcountdistinct-transact-sql"></a>APPROX_COUNT_DISTINCT (Transact-SQL)
[!INCLUDE[appliesto-xx-asdb-asdw-pdw-md](../../includes/appliesto-xx-asdb-asdw-pdw-md.md)]

Diese Funktion gibt die ungefähre Anzahl von eindeutigen Ungleich-Null-Werten in einer Gruppe zurück. 
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

> [!NOTE]
> APPROX_COUNT_DISTINCT ist ein öffentliches Vorschaufeature.  
  
## <a name="syntax"></a>Syntax  
  
```sql
-- Syntax for Azure SQL Database, Azure SQL Data Warehouse and Parallel Data Warehouse  

APPROX_COUNT_DISTINCT ( expression )   
```  
  
## <a name="arguments"></a>Argumente  
*expression*  
Eine [expression](../../t-sql/language-elements/expressions-transact-sql.md) beliebigen Typs mit Ausnahme von **image**, **sql_variant**, **ntext**oder **text**. 

## <a name="return-types"></a>Rückgabetypen
 **bigint**  
  
## <a name="remarks"></a>Remarks  
`APPROX_COUNT_DISTINCT( expression )` wertet einen Ausdruck für jede Zeile in einer Gruppe aus und gibt die geschätzte Anzahl der eindeutigen Werte in einer Gruppe zurück, die nicht NULL sind. Diese Funktion wurde entwickelt, um Aggregationen über große Datasets hinweg bereitzustellen, bei denen die Reaktionsfähigkeit wichtiger ist als die absolute Präzision.  

`APPROX_COUNT_DISTINCT` ist für den Einsatz in großen Datenszenarien konzipiert und für die folgenden Bedingungen optimiert:
- Zugriff auf Datasets, die aus Millionen von Zeilen oder mehr bestehen *und*
- Aggregation einer Spalte oder von Spalten mit vielen unterschiedlichen Werten

Die Funktionsimplementierung garantiert eine Fehlerquote von bis zu 2 % mit einer Wahrscheinlichkeit von 97 %. 

`APPROX_COUNT_DISTINCT` erfordert weniger Speicherplatz als ein vollständiger COUNT DISTINCT-Vorgang.  Angesichts des geringeren Speicherbedarfs ist es weniger wahrscheinlich, dass durch `APPROX_COUNT_DISTINCT` weniger Speicher zum Datenträger überläuft, als bei einem präzisen COUNT DISTINCT-Vorgang. 

> [!NOTE]
> Bei sortierungsbezogenen Zeichenfolgen verwendet die öffentliche Vorschauversion von APPROX_COUNT_DISTINCT einen binären Abgleich und liefert Ergebnisse, die bei Vorhandensein von BIN-Sortierungen und nicht von BIN2 erzeugt worden wären. 
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-approxcountdistinct"></a>A. Verwenden von APPROX_COUNT_DISTINCT 
Dieses Beispiel gibt die ungefähre Anzahl verschiedener Sortierschlüssel aus der Sortiertabelle zurück.
  
```sql
SELECT APPROX_COUNT_DISTINCT(O_OrderKey) AS Approx_Distinct_OrderKey
FROM dbo.Orders;
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Approx_Distinct_OrderKey
------------------------
15164704
```
  
### <a name="b-using-approxcountdistinct-with-group-by"></a>B. Verwenden von APPROX_COUNT_DISTINCT mit GROUP BY 
Dieses Beispiel gibt die ungefähre Anzahl verschiedener Sortierschlüssel geordnet nach Sortierstatus aus der Sortiertabelle zurück. 
  
```sql
SELECT O_OrderStatus, APPROX_COUNT_DISTINCT(O_OrderKey) AS Approx_Distinct_OrderKey
FROM dbo.Orders
GROUP BY O_OrderStatus
ORDER BY O_OrderStatus; 
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
O_OrderStatus                                                    Approx_Distinct_OrderKey
---------------------------------------------------------------- ------------------------
F                                                                7397838
O                                                                7387803
P                                                                388036
```
    
## <a name="see-also"></a>Siehe auch
[Aggregate Functions &#40;Transact-SQL&#41; (Aggregatfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[COUNT &#40;Transact-SQL&#41;](../../t-sql/functions/count-transact-sql.md) 
