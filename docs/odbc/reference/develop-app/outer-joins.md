---
title: Äußere Joins | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4bf875b3afd21f6b8cb211c999401b0ecb80879
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987811"
---
# <a name="outer-joins"></a>Äußere Verknüpfungen
ODBC unterstützt die Syntax von Left, Right und Full Outer Join von SQL-92. Die Escapesequenz für äußere Joins lautet:  
  
 **{OJ** _Outer-Join_**}**  
  
 Where *Outer Join* ist  
  
 *Tabellen Verweis* {**Left &#124; Right &#124; Full} äußerer Join** {*Table-Reference* &#124; *Outer-Join*} **auf** _Such Bedingung_  
  
 *Tabellen Verweis* gibt einen Tabellennamen an, und *Such Bedingung* gibt die Joinbedingung zwischen den *Tabellen verweisen*an.  
  
 Eine äußere joinanforderung muss nach dem **from** -Schlüsselwort und vor der **Where** -Klausel (sofern vorhanden) vorkommen. Umfassende Syntax Informationen finden Sie unter [Escapesequenz für äußere](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) Joins in Anhang C: SQL-Grammatik.  
  
 Die folgenden SQL-Anweisungen erstellen z. b. das gleiche Resultset, das alle Kunden auflistet, und zeigt an, welches über offene Aufträge verfügt. In der ersten Anweisung wird die Escapesequenzsyntax verwendet. Die zweite Anweisung verwendet die native Syntax für Oracle und ist nicht interoperabel.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Um die Typen von äußeren Joins zu ermitteln, die von einer Datenquelle und einem Treiber unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_OJ_CAPABILITIES-Flag auf. Die Typen von äußeren Joins, die unterstützt werden können, sind Left, right, Full oder netsted Outer Joins. äußere Joins, bei denen die Spaltennamen in der **on** -Klausel nicht die gleiche Reihenfolge wie ihre jeweiligen Tabellennamen in der **äußeren Join** -Klausel aufweisen. innere Joins in Verbindung mit äußeren Joins; und äußere Joins unter Verwendung eines beliebigen ODBC-Vergleichs Operators. Wenn der SQL_OJ_CAPABILITIES Informationstyp 0 zurückgibt, wird keine Outer Join-Klausel unterstützt.
