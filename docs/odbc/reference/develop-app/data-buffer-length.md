---
title: Datenpufferlänge | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- buffers [ODBC], data
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4a4e9a739201d74cfc6c4f7c18e64b91e0fabe4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305261"
---
# <a name="data-buffer-length"></a>Datenpufferlänge
Die Anwendung übergibt die Bytelänge des Datenpuffers an den Treiber in einem Argument namens *BufferLength* oder einem ähnlichen Namen. Beispielsweise gibt die Anwendung im folgenden Aufruf von **SQLBindCol**die Länge des *ValuePtr-Puffers* an (**size of(***ValuePtr***):**  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Ein Treiber gibt immer die Anzahl der Bytes und nicht die Anzahl der Zeichen im Argument Pufferlänge einer Funktion zurück, die über ein Ausgabezeichenfolgenargument verfügt.  
  
 Datenpufferlängen sind nur für Ausgabepuffer erforderlich. Der Treiber verwendet sie, um zu vermeiden, dass das Ende des Puffers überschrieben wird. Der Treiber überprüft die Datenpufferlänge jedoch nur, wenn der Puffer Daten mit variabler Länge enthält, z. B. Zeichen- oder Binärdaten. Wenn der Puffer Daten fester Länge enthält, z. B. eine ganze Zahl oder datumsstruktur, ignoriert der Treiber die Datenpufferlänge und geht davon aus, dass der Puffer groß genug ist, um die Daten zu halten. das heißt, es werden niemals Daten fester Länge abgeschnitten. Daher ist es wichtig, dass die Anwendung einen ausreichend großen Puffer für Daten fester Länge zuweist.  
  
 Wenn ein Abschneiden von Nicht-Datenausgabezeichenfolgen erfolgt (z. B. der für **SQLGetCursorName**zurückgegebene Cursorname), ist die zurückgegebene Länge im Argument Pufferlänge die maximal mögliche Zeichenlänge.  
  
 Datenpufferlängen sind für Eingabepuffer nicht erforderlich, da der Treiber nicht in diese Puffer schreibt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verwenden von Längen-/Indikatorwerten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Datenlänge, Pufferlänge und Abschneiden](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Zeichendaten und C-Zeichenfolgen](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
