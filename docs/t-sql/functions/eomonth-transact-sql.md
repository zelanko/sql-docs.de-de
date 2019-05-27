---
title: EOMONTH (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EOMONTH
- EOMONTH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EOMONTH function
ms.assetid: 1d060d8e-3297-4244-afef-57df2f8f92e2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e7fd4ca761d87df2a98a8c88ab0848ddff2e4faa
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65948843"
---
# <a name="eomonth-transact-sql"></a>EOMONTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Diese Funktion gibt den letzten Tag des Monats, der das angegebene Datum enthält, mit einer optionalen Abweichung zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
EOMONTH ( start_date [, month_to_add ] )  
```  
  
## <a name="arguments"></a>Argumente  
*start_date*  
Ein Datumsausdruck, der das Datum angibt, für das der letzte Tag des Monats zurückgegeben werden soll.  
  
*month_to_add*  
Ein optionaler ganzzahliger Ausdruck, der die Anzahl der Monate angibt, die zu *start_date* hinzugefügt werden sollen.  
  
Wenn das Argument *month_to_add* über einen Wert verfügt, fügt `EOMONTH` die angegebene Anzahl von Monaten zu *start_date* hinzu und gibt dann den letzten Tag des Monats für das sich ergebende Datum zurück. Wenn das Hinzufügen der gültigen Datumsbereiche einen Überlauf verursacht, löst `EOMONTH` einen Fehler aus.  
  
## <a name="return-type"></a>Rückgabetyp  
 **Datum**  
  
## <a name="remarks"></a>Remarks  
Die Funktion `EOMONTH` kann auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Servern und höher remote ausgeführt werden. Sie kann nicht auf Servern mit einer niedrigeren Version als [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] remote ausgeführt werden.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-eomonth-with-explicit-datetime-type"></a>A. EOMONTH mit explizitem datetime-Typ  
  
```  
DECLARE @date DATETIME = '12/1/2011';  
SELECT EOMONTH ( @date ) AS Result;  
GO  
```  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
2011-12-31  
  
(1 row(s) affected)  
```  

### <a name="b-eomonth-with-string-parameter-and-implicit-conversion"></a>B. EOMONTH mit Zeichenfolgenparameter und impliziter Konvertierung  
  
```  
DECLARE @date VARCHAR(255) = '12/1/2011';  
SELECT EOMONTH ( @date ) AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
2011-12-31  
  
(1 row(s) affected)  
```  
  
### <a name="c-eomonth-with-and-without-the-monthtoadd-parameter"></a>C. EOMONTH mit und ohne den month_to_add-Parameter  
  
Hinweis: Die in diesen Resultsets gezeigten Werte stellen ein Ausführungsdatum zwischen und einschließlich der folgenden dar:
        
        12/01/2011
        
        and
        
        12/31/2011

```sql  
DECLARE @date DATETIME = GETDATE();  
SELECT EOMONTH ( @date ) AS 'This Month';  
SELECT EOMONTH ( @date, 1 ) AS 'Next Month';  
SELECT EOMONTH ( @date, -1 ) AS 'Last Month';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
This Month  
-----------------------  
2011-12-31  
  
(1 row(s) affected)  
  
Next Month  
-----------------------  
2012-01-31  
  
(1 row(s) affected)  
  
Last Month  
-----------------------  
2011-11-30  
  
(1 row(s) affected)  
```  
  
  

