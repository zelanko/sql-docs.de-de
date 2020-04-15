---
title: Fehler und Batches | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300430"
---
# <a name="errors-and-batches"></a>Fehler und Batches
Wenn beim Ausführen eines Batches von SQL-Anweisungen ein Fehler auftritt, ist eines der folgenden vier Ergebnisse möglich. (Jedes mögliche Ergebnis ist datenquellenspezifisch und kann sogar von den Anweisungen abhängen, die im Batch enthalten sind.)  
  
-   Es werden keine Anweisungen im Batch ausgeführt.  
  
-   Es werden keine Anweisungen im Batch ausgeführt, und für die Transaktion wird ein Rollback ausgeführt.  
  
-   Alle Anweisungen vor der Fehleranweisung werden ausgeführt.  
  
-   Alle Anweisungen mit Ausnahme der Fehleranweisung werden ausgeführt.  
  
 In den ersten beiden Fällen geben **SQLExecute** und **SQLExecDirect** SQL_ERROR zurück. In den beiden letztgenannten Fällen können sie je nach Umsetzung SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgeben. In allen Fällen können weitere Fehlerinformationen mit **SQLGetDiagField**, **SQLGetDiagRec**oder **SQLError**abgerufen werden. Art und Tiefe dieser Informationen sind jedoch datenquellenspezifisch. Darüber hinaus ist es unwahrscheinlich, dass diese Informationen die Anweisung irrtümlich genau identifizieren.
