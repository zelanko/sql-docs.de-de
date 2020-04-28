---
title: Datenpuffer Adresse | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305271"
---
# <a name="data-buffer-address"></a>Adresse des Datenpuffers
Die Anwendung übergibt die Adresse des Daten Puffers an den Treiber in einem Argument, das häufig als *ValuePtr* oder ein ähnlicher Name bezeichnet wird. Im folgenden Befehl von **SQLBindCol**gibt die Anwendung z. b. die Adresse der *Date* -Variablen an:  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Wie im Abschnitt [zuordnen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) erwähnt, muss die Adresse eines verzögerten Puffers gültig bleiben, bis der Puffer nicht gebunden ist.  
  
 Wenn Sie nicht ausdrücklich verboten ist, kann die Adresse eines Daten Puffers ein NULL-Zeiger sein. Für Puffer, die zum Senden von Daten an den Treiber verwendet werden, bewirkt dies, dass der Treiber die Informationen ignoriert, die normalerweise im Puffer enthalten sind. Für Puffer, die zum Abrufen von Daten aus dem Treiber verwendet werden, bewirkt dies, dass der Treiber keinen Wert zurückgibt. In beiden Fällen ignoriert der Treiber das entsprechende Argument für die Datenpuffer Länge.
