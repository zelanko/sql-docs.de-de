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
manager: craigg
ms.openlocfilehash: cd35a8bd0e2a9280d16614a3979dc2af05487e42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47619608"
---
# <a name="outer-joins"></a>Äußere Verknüpfungen
ODBC unterstützt die SQL-92 linke, Rechte und vollständige äußere Join-Syntax. Die Escapesequenz für äußere Joins lautet  
  
 **{ABl.** *outer-Joins ***}**  
  
 wo *äußere Join* ist  
  
 *Tabellenverweis* {**Links &#124; rechts &#124; vollständige} INKLUSIONSVERKNÜPFUNGS** {*Tabellenverweis* &#124; *äußere Join*} **ON**  *Bedingung*  
  
 *Tabellenverweis* gibt an, einen Tabellennamen ein, und *Suchbedingung* gibt an, die Join-Bedingung zwischen der *Tabellenverweise*.  
  
 Anforderung für einen äußeren Join muss nach angezeigt werden die **FROM** Schlüsselwort und vor der **, in denen** Klausel (falls vorhanden). Weitere Informationen über die vollständige Syntax, finden Sie unter [äußeren Join Escape Sequence](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) in Anhang C: SQL-Grammatik.  
  
 Die folgenden SQL-Anweisungen erstellen z. B. das gleiche Resultset, das Listet alle Kunden und zeigt die offenen Aufträge hat. Die erste Anweisung verwendet die Syntax der Escapesequenz. Die zweite Anweisung verwendet die systemeigene Syntax für Oracle und ist nicht interoperabel.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Um die Arten von äußeren Verknüpfungen zu bestimmen, die eine Datenquelle und den Treiber zu unterstützen, eine Anwendung ruft **SQLGetInfo** mit der SQL_OJ_CAPABILITIES-flag. Die Arten von äußeren Verknüpfungen, die unterstützt werden möglicherweise Links sind, rechts, vollständige oder geschachtelte äußere Joins; äußere Joins in der die im Spaltennamen die **ON** Klausel müssen sich nicht auf die gleiche Reihenfolge wie ihre entsprechenden Tabellennamen in der **OUTER JOIN** -Klausel; innere Joins zusammen mit äußeren Joins; und äußeren Joins verwenden alle ODBC-Vergleichsoperator. Wenn der Typ der SQL_OJ_CAPABILITIES Informationen 0 zurückgibt, wird keine äußeren Join-Klausel unterstützt.
