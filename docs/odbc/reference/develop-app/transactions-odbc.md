---
title: ODBC-Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], about transactions
- transactions [ODBC]
ms.assetid: b4ca861a-c164-4e87-8672-d5de15e3823c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6ce5decd2744c0ce9d753e355321a40d00fd620
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305811"
---
# <a name="transactions-odbc"></a>Transaktions-ODBC
Ein *Transaktion* ist eine Arbeitseinheit, die erfolgt im einem einzigen atomaren Vorgang; d. h. der Vorgang erfolgreich ausgeführt wird, oder ein Fehler auftritt, als Ganzes. Betrachten Sie z. B. Geld von einem Bankkonto auf einen anderen zu übertragen. Dies umfasst zwei Schritte: bucht Geld von das erste Konto und zahlt es sie in der Sekunde. Es ist wichtig, dass beide Schritte erfolgreich ausgeführt. Es ist nicht für einen Schritt erfolgreich ausgeführt werden kann und die andere nicht zulässig. Eine Datenbank, die Transaktionen unterstützt, ist dies gewährleisten können.  
  
 Transaktionen abgeschlossen werden können, indem Sie entweder *Commit* oder *Rollback*. Wenn eine Transaktion ein Commit ausgeführt wird, die Änderungen, die in dieser Transaktion permanent gemacht werden. Beim Rollback einer Transaktions ausgeführt wird, werden die betroffenen Zeilen in den Zustand zurückgegeben, denen sie hatten, bevor die Transaktion gestartet wurde. Um das Konto übertragen Beispiel erweitern, führt eine Anwendung eine SQL-Anweisung das erste Konto belastet und einer anderen SQL­Anweisung das zweite Konto Gutschrift. Wenn beide Anweisungen erfolgreich ausgeführt werden, führt die Anwendung dann Commit der Transaktion. Aber wenn entweder Anweisung aus irgendeinem Grund fehlschlägt, die Anwendung ein Rollback die Transaktion. In beiden Fällen wird die Anwendung einen konsistenten Zustand am Ende der Transaktion sichergestellt.  
  
 Eine einzelne Transaktion kann mehrere Datenbankvorgänge umfassen, die zu unterschiedlichen Zeiten auftreten. Wenn andere Transaktionen über vollständigen Zugriff auf die Zwischenergebnisse hatten, möglicherweise die Transaktionen gegenseitig beeinträchtigen. Beispielsweise angenommen, eine Transaktion eine Zeile einfügt, liest eine zweite Transaktion die Zeile, und die erste Transaktion zurückgesetzt wird. Die zweite Transaktion jetzt hat Daten für eine Zeile, die nicht vorhanden ist.  
  
 Um dieses Problem zu beheben, gibt es verschiedene Schemas zum Transaktionen voneinander zu isolieren. *Transaktionsisolation* wird in der Regel implementiert, durch Sperren von Zeilen, die mehr als eine Transaktion von der Verwendung der gleichen Zeile zur gleichen Zeit ausschließt. In einigen Datenbanken kann eine Zeile Sperren auch andere Zeilen gesperrt werden.  
  
 Erhöhte Transaction Isolation Lieferumfang reduzierten *Parallelität* oder die Fähigkeit von zwei Transaktionen, die gleichen Daten zur gleichen Zeit zu verwenden. Weitere Informationen finden Sie unter [Festlegen der Isolationsstufe für Transaktionen](../../../odbc/reference/develop-app/setting-the-transaction-isolation-level.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Transaktionen in ODBC](../../../odbc/reference/develop-app/transactions-in-odbc-odbc.md)  
  
-   [Transaktionsisolation](../../../odbc/reference/develop-app/transaction-isolation.md)  
  
-   [Parallelitätssteuerung](../../../odbc/reference/develop-app/concurrency-control.md)
