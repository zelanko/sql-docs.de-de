---
title: Fehler und Batches | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6902b82c74e953d6009d7e5352608477d92122d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68051130"
---
# <a name="errors-and-batches"></a>Fehler und Batches
Wenn ein Fehler auftritt, während ein Batch von SQL-Anweisungen ausgeführt wird, kann eines der folgenden vier Ergebnisse auftreten. (Jedes mögliche Ergebnis ist Datenquellen spezifisch und kann sogar von den Anweisungen abhängen, die im Batch enthalten sind.)  
  
-   Es werden keine Anweisungen im Batch ausgeführt.  
  
-   Es werden keine Anweisungen im Batch ausgeführt, und für die Transaktion wird ein Rollback ausgeführt.  
  
-   Alle-Anweisungen vor der Fehler Anweisung werden ausgeführt.  
  
-   Alle-Anweisungen außer der Error-Anweisung werden ausgeführt.  
  
 In den ersten beiden Fällen geben **SQLExecute** und **SQLExecDirect** SQL_ERROR zurück. In den letzten beiden Fällen können Sie abhängig von der Implementierung SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgeben. In allen Fällen können weitere Fehlerinformationen mit **SQLGetDiagField**, **SQLGetDiagRec**oder **SQLError**abgerufen werden. Die Art und Tiefe dieser Informationen sind jedoch Datenquellen spezifisch. Darüber hinaus ist es unwahrscheinlich, dass diese Informationen die Anweisung fehlerhaft erkennen.
