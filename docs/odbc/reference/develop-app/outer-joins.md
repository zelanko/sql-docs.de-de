---
title: Äußere Verbindungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 81988d34dca38d5c041ff9f87e9674d7c97d76cc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282445"
---
# <a name="outer-joins"></a>Äußere Verknüpfungen
ODBC unterstützt die SQL-92-Syntax für linke, rechte und vollständige äußere Verknüpfungen. Die Escape-Sequenz für äußere Verknüpfungen ist  
  
 _Abl.-Abl._**}** **{oj**  
  
 wo *die äußere Verknüpfung*  
  
 *Tabellen-Referenz* - LINKS **&#124; RECHTS &#124; FULL- OUTER JOIN-** *&#124;-Outer-Join-* **ON** _search-condition_ *table-reference*  
  
 *table-reference* gibt einen Tabellennamen an, und *die Suchbedingung* gibt die Verknüpfungsbedingung zwischen den *Tabellenreferenzen*an.  
  
 Eine äußere Join-Anforderung **FROM** muss nach dem FROM-Schlüsselwort und vor der **WHERE-Klausel** (falls vorhanden) angezeigt werden. Vollständige Syntaxinformationen finden Sie unter [Outer Join Escape Sequence](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) in Anhang C: SQL Grammar.  
  
 Die folgenden SQL-Anweisungen erstellen z. B. dasselbe Resultset, das alle Kunden auflistet und anzeigt, welche offenen Aufträge vorliegen. Die erste Anweisung verwendet die Escape-Sequenz-Syntax. Die zweite Anweisung verwendet die systemeigene Syntax für Oracle und ist nicht interoperabel.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Um die Typen von äußeren Verknüpfungen zu bestimmen, die von einer Datenquelle und einem Treiber unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_OJ_CAPABILITIES-Flag auf. Die Typen der äußeren Verknüpfungen, die unterstützt werden können, sind linke, rechte, vollständige oder verschachtelte äußere Verknüpfungen. äußere Verknüpfungen, bei denen die Spaltennamen in der **ON-Klausel** nicht die gleiche Reihenfolge wie ihre jeweiligen Tabellennamen in der **OUTER JOIN-Klausel** aufweisen; innere Verbindungen in Verbindung mit äußeren Verbindungen; und äußere Verknüpfungen mit einem beliebigen ODBC-Vergleichsoperator. Wenn der SQL_OJ_CAPABILITIES-Informationstyp 0 zurückgibt, wird keine äußere Join-Klausel unterstützt.
