---
title: Adresse des Datenpuffers | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7cd157edd6111dec29ae238a1c383879e66ac0b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067429"
---
# <a name="data-buffer-address"></a>Adresse des Datenpuffers
Die Anwendung übergibt die Adresse des Datenpuffers an den Treiber in einem Argument, das häufig mit dem Namen *ValuePtr* oder einem ähnlichen Namen. Z. B. in den folgenden Aufruf von **SQLBindCol**, die Anwendung gibt die Adresse der *Datum* Variable:  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Siehe die [zuweisen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) die Adresse eines Puffers verzögerte-Abschnitt muss gültig bleiben, bis der Puffer aufgehoben wird.  
  
 Es sei denn, sie insbesondere nicht zulässig ist, kann die Adresse eines Datenpuffers mit ein null-Zeiger sein. Für Puffer zum Senden von Daten an den Treiber verwendet bewirkt, dass dies den Treiber, die normalerweise im Puffer enthaltenen Informationen zu ignorieren. Für Puffer zum Abrufen von Daten aus dem Treiber verwendet bewirkt, dass dies den Treiber, die keinen Wert zurückgibt. In beiden Fällen ignoriert der Treiber die entsprechenden Daten Puffer Length-Argument.
