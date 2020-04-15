---
title: Transaktionen ODBC | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a40c34b2abeb346c7a718994ba2484bfc728e2b1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297955"
---
# <a name="transactions-odbc"></a>Transaktions-ODBC
Eine *Transaktion* ist eine Arbeitseinheit, die als einziger atomarer Vorgang ausgeführt wird. das heißt, der Vorgang ist erfolgreich oder schlägt als Ganzes fehl. Erwägen Sie beispielsweise, Geld von einem Bankkonto auf ein anderes zu überweisen. Dies umfasst zwei Schritte: das Geld vom ersten Konto abzuheben und es im zweiten einzuzahlen. Es ist wichtig, dass beide Schritte erfolgreich sind; es ist nicht akzeptabel, dass ein Schritt erfolgreich ist und der andere scheitert. Eine Datenbank, die Transaktionen unterstützt, kann dies garantieren.  
  
 Transaktionen können abgeschlossen werden, indem entweder *festgeschrieben* oder *ein Rollback ausgeführt*wird. Wenn eine Transaktion festgeschrieben wird, werden die in dieser Transaktion vorgenommenen Änderungen dauerhaft. Wenn für eine Transaktion ein Rollback ausgeführt wird, werden die betroffenen Zeilen in den Zustand zurückgeführt, in dem sie sich vor dem Start der Transaktion befanden. Um das Beispiel für die Kontoübertragung zu erweitern, führt eine Anwendung eine SQL-Anweisung aus, um das erste Konto und eine andere SQL-Anweisung zu belasten, um das zweite Konto gutzuschreiben. Wenn beide Anweisungen erfolgreich sind, überträgt die Anwendung die Transaktion. Wenn jedoch eine der beiden Anweisungsausfällen aus irgendeinem Grund fehlschlägt, führt die Anwendung einen Rollback für die Transaktion durch. In beiden Fällen garantiert die Anwendung einen konsistenten Zustand am Ende der Transaktion.  
  
 Eine einzelne Transaktion kann mehrere Datenbankvorgänge umfassen, die zu unterschiedlichen Zeiten ausgeführt werden. Wenn andere Transaktionen vollständigen Zugriff auf die Zwischenergebnisse hatten, können die Transaktionen einander stören. Angenommen, eine Transaktion fügt eine Zeile ein, eine zweite Transaktion liest diese Zeile, und die erste Transaktion wird zurückgesetzt. Die zweite Transaktion enthält nun Daten für eine Zeile, die nicht vorhanden ist.  
  
 Um dieses Problem zu lösen, gibt es verschiedene Schemata, um Transaktionen voneinander zu isolieren. *Die Transaktionsisolation* wird im Allgemeinen durch Sperren von Zeilen implementiert, wodurch mehrere Transaktionen daran gehindert werden, dieselbe Zeile gleichzeitig zu verwenden. In einigen Datenbanken kann das Sperren einer Zeile auch andere Zeilen sperren.  
  
 Mit zunehmender Transaktionsisolation kommt reduzierte *Parallelität* oder die Fähigkeit von zwei Transaktionen, dieselben Daten gleichzeitig zu verwenden. Weitere Informationen finden Sie unter [Festlegen der Transaktionsisolationsstufe](../../../odbc/reference/develop-app/setting-the-transaction-isolation-level.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Transaktionen in ODBC](../../../odbc/reference/develop-app/transactions-in-odbc-odbc.md)  
  
-   [Transaktionsisolation](../../../odbc/reference/develop-app/transaction-isolation.md)  
  
-   [Parallelitätskontrolle](../../../odbc/reference/develop-app/concurrency-control.md)
