---
title: RAND (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RAND
- RAND_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RAND function
- values [SQL Server], random float
- random float value
ms.assetid: 363c84d6-b9fa-49ba-9a75-e44f27535ff6
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6f69b3aadea5a426cc478eadd9c3228242161060
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87111346"
---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Gibt einen **float**-Pseudozufallswert von ausschließlich 0 bis 1 zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RAND ( [ seed ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *seed*  
 Ein ganzzahliger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) (**tinyint**, **smallint** oder **int**), der den Ausgangswert zurückgibt. Wenn *seed* nicht angegeben ist, weist [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] einen zufälligen Ausgangswert zu. Für einen bestimmten Ausgangswert ist das zurückgegebene Ergebnis immer gleich.  
  
## <a name="return-types"></a>Rückgabetypen  
 **float**  
  
## <a name="remarks"></a>Bemerkungen  
 Bei wiederholten Aufrufen von RAND() mit demselben Ausgangswert werden dieselben Ergebnisse zurückgegeben.  
  
 Wenn für eine bestimmte Verbindung RAND() mit einem angegebenen Ausgangswert aufgerufen wird, führen alle nachfolgenden Aufrufe von RAND() zu Ergebnissen, die auf dem RAND()-Ausgangsaufruf basieren. Durch die folgende Abfrage wird z. B. immer dieselbe Nummernreihenfolge zurückgegeben.  
  
```sql  
SELECT RAND(100), RAND(), RAND()   
```  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel führt zu vier Zufallszahlen, die von der RAND-Funktion generiert werden.  
  
```sql  
DECLARE @counter SMALLINT;  
SET @counter = 1;  
WHILE @counter < 5  
   BEGIN  
      SELECT RAND() Random_Number  
      SET @counter = @counter + 1  
   END;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mathematische Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
