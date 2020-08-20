---
description: Fehler und Batches
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
ms.openlocfilehash: 1e5cdf4d394ffa1c17173aedc4485b6979cf371e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461492"
---
# <a name="errors-and-batches"></a>Fehler und Batches
Wenn ein Fehler auftritt, während ein Batch von SQL-Anweisungen ausgeführt wird, kann eines der folgenden vier Ergebnisse auftreten. (Jedes mögliche Ergebnis ist Datenquellen spezifisch und kann sogar von den Anweisungen abhängen, die im Batch enthalten sind.)  
  
-   Es werden keine Anweisungen im Batch ausgeführt.  
  
-   Es werden keine Anweisungen im Batch ausgeführt, und für die Transaktion wird ein Rollback ausgeführt.  
  
-   Alle-Anweisungen vor der Fehler Anweisung werden ausgeführt.  
  
-   Alle-Anweisungen außer der Error-Anweisung werden ausgeführt.  
  
 In den ersten beiden Fällen geben **SQLExecute** und **SQLExecDirect** SQL_ERROR zurück. In den letzten beiden Fällen können Sie abhängig von der Implementierung SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgeben. In allen Fällen können weitere Fehlerinformationen mit **SQLGetDiagField**, **SQLGetDiagRec**oder **SQLError**abgerufen werden. Die Art und Tiefe dieser Informationen sind jedoch Datenquellen spezifisch. Darüber hinaus ist es unwahrscheinlich, dass diese Informationen die Anweisung fehlerhaft erkennen.
