---
title: Transaktionen ODBC | Microsoft-Dokumentation
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
ms.openlocfilehash: 521a2ffbf0f8eb5e2590ae6e42d50dc71d536683
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086044"
---
# <a name="transactions-odbc"></a>Transaktions-ODBC
Eine *Transaktion* ist eine Arbeitseinheit, die als einzelner, atomarer Vorgang durchgeführt wird. Das heißt, dass der Vorgang erfolgreich ist oder als Ganzes fehlschlägt. Beispielsweise können Sie Geld von einem Bankkonto auf ein anderes Konto übertragen. Dies umfasst zwei Schritte: das Zurückziehen des Geldes aus dem ersten Konto und das Ablegen des Geldes in der zweiten. Es ist wichtig, dass beide Schritte erfolgreich ausgeführt werden. Es ist nicht zulässig, dass ein Schritt erfolgreich ist und der andere fehlschlägt. Eine Datenbank, die Transaktionen unterstützt, kann dies gewährleisten.  
  
 Transaktionen können ausgeführt werden, indem entweder *ein* Commit oder ein *Rollback*ausgeführt wird. Wenn für eine Transaktion ein Commit ausgeführt wird, werden die in dieser Transaktion vorgenommenen Änderungen als permanent festgestellt. Wenn für eine Transaktion ein Rollback ausgeführt wird, werden die betroffenen Zeilen in den Zustand zurückversetzt, in dem Sie sich vor dem Start der Transaktion befanden. Zum Erweitern des Beispiels für die Konto Übertragung führt eine Anwendung eine SQL-Anweisung aus, um das erste Konto zu belasten, und eine andere SQL-Anweisung, um das zweite Konto gutzuschreiben. Wenn beide Anweisungen erfolgreich sind, führt die Anwendung einen Commit für die Transaktion aus. Wenn die Anweisung jedoch aus irgendeinem Grund fehlschlägt, führt die Anwendung ein Rollback der Transaktion aus. In beiden Fällen garantiert die Anwendung am Ende der Transaktion einen konsistenten Zustand.  
  
 Eine einzelne Transaktion kann mehrere Daten Bank Vorgänge umfassen, die zu unterschiedlichen Zeiten stattfinden. Wenn andere Transaktionen einen vollen Zugriff auf die Zwischenergebnisse haben, können sich die Transaktionen gegenseitig stören. Angenommen, eine Transaktion fügt eine Zeile ein, eine zweite Transaktion liest diese Zeile, und für die erste Transaktion wird ein Rollback ausgeführt. Die zweite Transaktion enthält jetzt Daten für eine Zeile, die nicht vorhanden ist.  
  
 Um dieses Problem zu beheben, gibt es verschiedene Schemas, um Transaktionen voneinander zu isolieren. Die *Transaktions Isolation* wird in der Regel durch Sperren von Zeilen implementiert, wodurch verhindert wird, dass mehr als eine Transaktion dieselbe Zeile gleichzeitig verwendet. In einigen Datenbanken können durch Sperren einer Zeile auch andere Zeilen gesperrt werden.  
  
 Bei einer verstärkten Transaktions Isolation kommt es zu eingeschränkter Parallelität *,* oder die Fähigkeit von zwei Transaktionen, dieselben Daten gleichzeitig zu verwenden. Weitere Informationen finden Sie unter [Festlegen der Transaktions Isolationsstufe](../../../odbc/reference/develop-app/setting-the-transaction-isolation-level.md).  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Transaktionen in ODBC](../../../odbc/reference/develop-app/transactions-in-odbc-odbc.md)  
  
-   [Transaktionsisolation](../../../odbc/reference/develop-app/transaction-isolation.md)  
  
-   [Gleichzeitigkeitssteuerung](../../../odbc/reference/develop-app/concurrency-control.md)
