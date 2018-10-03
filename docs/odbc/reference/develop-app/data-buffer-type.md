---
title: Typ des Datenpuffers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a54054387a57d59470bae6d982b5ce700362f483
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635388"
---
# <a name="data-buffer-type"></a>Datenpuffertyp
Die C-Datentyp eines Puffers, die von der Anwendung angegeben ist. Mit einer einzelnen Variablen geschieht dies, wenn die Anwendung die Variable weist. Mit generischen Arbeitsspeicher –, also Arbeitsspeicher verweist einen Zeiger vom Typ "void" — Dies geschieht, wenn die Anwendung den Arbeitsspeicher für eine bestimmte Art umgewandelt. Der Treiber ermittelt, dieser Typ gibt es zwei Möglichkeiten:  
  
-   **-Datentypargument Puffer.** Zur Übertragung von Parameterwerten und Resultsetdaten, verwendet werden, z. B. der Puffer mit gebundenen Puffer *TargetValuePtr* in **SQLBindCol**, besitzen in der Regel ein Argument zugeordneten Typ wie z. B. die  *TargetType* -Argument in **SQLBindCol**. In diesem Argument und übergibt die Anwendung der C-Typ-ID, die entspricht, in den Typ des Puffers. Z. B. in den folgenden Aufruf von **SQLBindCol**, der Wert SQL_C_TYPE_DATE weist den Treiber, die die *Datum* Puffer ist ein SQL_DATE_STRUCT:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Weitere Informationen zu Typ-IDs finden Sie unter den [Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md) weiter unten in diesem Abschnitt.  
  
-   **Der vordefinierte Typ.** Puffer zum Senden und Abrufen von Optionen oder Attribute, z. B. den Puffer verweist die *InfoValuePtr* -Argument in **SQLGetInfo**, haben Sie einen festen Typ, der von der angegebenen Option abhängig ist. Der Treiber wird davon ausgegangen, dass der Datenpuffer dieses Typs ist; Es ist Aufgabe der Anwendung, um einen Puffer dieses Typs zuzuweisen. Zum Beispiel in der folgenden aufrufen, um **SQLGetInfo**, der Treiber geht davon aus, der Puffer ist eine 32-Bit-Ganzzahl, da es sich handelt, was die SQL_STRING_FUNCTIONS-Option ist erforderlich:  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Der Treiber verwendet die C-Datentyp zum Interpretieren der Daten im Puffer.
