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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36a402686a695a08748df24a7b40a228d7a2ca7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300430"
---
# <a name="errors-and-batches"></a>Fehler und Batches
Wenn ein Fehler auftritt, während ein Batch von SQL-Anweisungen ausgeführt wird, kann eines der folgenden vier Ergebnisse auftreten. (Jedes mögliche Ergebnis ist Datenquellen spezifisch und kann sogar von den Anweisungen abhängen, die im Batch enthalten sind.)  
  
-   Es werden keine Anweisungen im Batch ausgeführt.  
  
-   Es werden keine Anweisungen im Batch ausgeführt, und für die Transaktion wird ein Rollback ausgeführt.  
  
-   Alle-Anweisungen vor der Fehler Anweisung werden ausgeführt.  
  
-   Alle-Anweisungen außer der Error-Anweisung werden ausgeführt.  
  
 In den ersten beiden Fällen geben **SQLExecute** und **SQLExecDirect** SQL_ERROR zurück. In den letzten beiden Fällen können Sie abhängig von der Implementierung SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgeben. In allen Fällen können weitere Fehlerinformationen mit **SQLGetDiagField**, **SQLGetDiagRec**oder **SQLError**abgerufen werden. Die Art und Tiefe dieser Informationen sind jedoch Datenquellen spezifisch. Darüber hinaus ist es unwahrscheinlich, dass diese Informationen die Anweisung fehlerhaft erkennen.
