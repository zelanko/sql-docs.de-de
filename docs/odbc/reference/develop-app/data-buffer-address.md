---
title: Datenpufferadresse | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578e4e37a78818cb640d9f32e2480cec5951df63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305271"
---
# <a name="data-buffer-address"></a>Adresse des Datenpuffers
Die Anwendung übergibt die Adresse des Datenpuffers an den Treiber in einem Argument, das häufig *ValuePtr* oder einen ähnlichen Namen genannt wird. Beispielsweise gibt die Anwendung im folgenden Aufruf von **SQLBindCol**die Adresse der *Date-Variablen* an:  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Wie im Abschnitt Zuweisen und Verteilen von Puffern erwähnt, muss die Adresse eines [verzögerten Puffers](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) gültig bleiben, bis der Puffer ungebunden ist.  
  
 Sofern dies nicht ausdrücklich verboten ist, kann die Adresse eines Datenpuffers ein Nullzeiger sein. Bei Puffern, die zum Senden von Daten an den Treiber verwendet werden, ignoriert der Treiber die normalerweise im Puffer enthaltenen Informationen. Bei Puffern, die zum Abrufen von Daten vom Treiber verwendet werden, gibt der Treiber keinen Wert zurück. In beiden Fällen ignoriert der Treiber das entsprechende Argument für die Datenpufferlänge.
