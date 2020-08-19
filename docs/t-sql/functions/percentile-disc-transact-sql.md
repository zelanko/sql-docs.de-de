---
description: PERCENTILE_DISC (Transact-SQL)
title: PERCENTILE_DISC (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/20/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PERCENTILE_DISC
- PERCENTILE_DISC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PERCENTILE_DISC function
- analytic functions,PERCENTILE_DISC
ms.assetid: b545413d-c4f7-4c8e-8617-607599a26680
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: aba51bed39dc07ce130e22c6e701c8ada754e4f1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88445673"
---
# <a name="percentile_disc-transact-sql"></a>PERCENTILE_DISC (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Berechnet für sortierte Werte in einem gesamten Rowset oder innerhalb bestimmter Partitionen eines Rowsets in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein bestimmtes Quantil. Für den angegebenen Quantilwert sortiert *P*, PERCENTILE_DISC die Ausdruckswerte in der ORDER BY-Klausel. Es wird dann der Wert mit dem kleinsten angegebenen CUME_DIST-Wert (in Bezug auf die gleiche Sortierspezifikation) zurückgegeben, der größer oder gleich *P* ist. Beispiel: PERCENTILE_DISC (0.5) berechnet das 50. Quantil (d.h. den Mittelwert) eines Ausdrucks. PERCENTILE_DISC berechnet das Quantil auf Grundlage einer diskreten Verteilung der Spaltenwerte. Das Ergebnis entspricht einem bestimmten Wert in der Spalte.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
PERCENTILE_DISC ( numeric_literal ) WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *literal*  
 Das zu berechnende Quantil. Der Wert muss zwischen 0,0 und 1,0 liegen.  
  
 WITHIN GROUP **(** ORDER BY *order_by_expression* [ **ASC** | DESC)**  
 Gibt eine Liste von numerischen Werten für die Sortierung und Berechnung des Quantils an. Es ist nur ein *order_by_expression*-Element zulässig. Standardmäßig wird die Sortierung in aufsteigender Reihenfolge vorgenommen. Die Liste der Werte kann von einem beliebigen Datentyp sein, der für den Sortierungsvorgang gültig sein kann.  
  
 OVER **(** \<partition_by_clause>)**  
 Teilt die Ergebnisse der FROM-Klausel in Partitionen. Die Quantilfunktion wird auf diese Partitionen angewendet. Weitere Informationen finden Sie unter [OVER-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md). \<ORDER BY clause> und \<rows or range clause> können nicht in PERCENTILE_DISC-Funktionen angegeben werden.  
  
## <a name="return-types"></a>Rückgabetypen  
 Der Rückgabetyp wird durch den *order_by_expression*-Typ bestimmt.  
  
## <a name="compatibility-support"></a>Kompatibilitätsunterstützung  
 Unter Kompatibilitätsgrad 110 und höher ist WITHIN GROUP ein reserviertes Schlüsselwort. Weitere Informationen finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Alle NULL-Werte im Dataset werden ignoriert.  
  
 PERCENTILE_DISC ist nicht deterministisch. Weitere Informationen finden Sie unter [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="basic-syntax-example"></a>Einfaches Syntaxbeispiel  

 Im folgenden Beispiel wird das durchschnittliche Mitarbeitergehalt in jeder Abteilung mithilfe von PERCENTILE_CONT und PERCENTILE_DISC ermittelt. Sie geben möglicherweise nicht den gleichen Wert zurück:
* PERCENTILE_CONT gibt den entsprechenden Wert zurück, auch wenn er im Datenset nicht vorhanden ist.
* PERCENTILE_DISC gibt einen tatsächlich festgelegten Wert zurück.  
  
```  
USE AdventureWorks2012;  
  
SELECT DISTINCT Name AS DepartmentName  
      ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianCont  
      ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianDisc  
FROM HumanResources.Department AS d  
INNER JOIN HumanResources.EmployeeDepartmentHistory AS dh   
    ON dh.DepartmentID = d.DepartmentID  
INNER JOIN HumanResources.EmployeePayHistory AS ph  
    ON ph.BusinessEntityID = dh.BusinessEntityID  
WHERE dh.EndDate IS NULL;  
```  
  
 Dies ist ein Auszug aus dem Resultset.  
  
 ```
DepartmentName        MedianCont    MedianDisc
--------------------   ----------   ----------
Document Control       16.8269      16.8269
Engineering            34.375       32.6923
Executive              54.32695     48.5577
Human Resources        17.427850    16.5865
```
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="basic-syntax-example"></a>Einfaches Syntaxbeispiel  

 Im folgenden Beispiel wird das durchschnittliche Mitarbeitergehalt in jeder Abteilung mithilfe von PERCENTILE_CONT und PERCENTILE_DISC ermittelt. Sie geben möglicherweise nicht den gleichen Wert zurück:
* PERCENTILE_CONT gibt den entsprechenden Wert zurück, auch wenn er im Datenset nicht vorhanden ist. 
* PERCENTILE_DISC gibt einen tatsächlich festgelegten Wert zurück.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT DepartmentName  
       ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianCont  
       ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianDisc  
FROM dbo.DimEmployee;  
  
```  
  
 Dies ist ein Auszug aus dem Resultset.  
  
 ```
DepartmentName        MedianCont    MedianDisc  
--------------------   ----------   ----------  
Document Control       16.826900    16.8269  
Engineering            34.375000    32.6923  
Human Resources        17.427850    16.5865  
Shipping and Receiving  9.250000     9.0000
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [PERCENTILE_CONT &#40;Transact-SQL&#41;](../../t-sql/functions/percentile-cont-transact-sql.md)  
  
  


