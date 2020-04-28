---
title: Länge des Daten Puffers | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305261"
---
# <a name="data-buffer-length"></a>Datenpufferlänge
Die Anwendung übergibt die Byte Länge des Daten Puffers an den Treiber in einem Argument mit dem Namen *BufferLength* oder einem ähnlichen Namen. Beispielsweise gibt die Anwendung im folgenden Befehl von **SQLBindCol**die Länge des *ValuePtr* -Puffers (**sizeof (***ValuePtr***)**) an:  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Ein Treiber gibt immer die Anzahl von Bytes und nicht die Anzahl der Zeichen im Puffer Längenargument einer Funktion zurück, die über ein Output String-Argument verfügt.  
  
 Datenpuffer Längen sind nur für Ausgabepuffer erforderlich. der Treiber verwendet diese, um das Schreiben über das Ende des Puffers zu vermeiden. Der Treiber prüft die Länge des Daten Puffers jedoch nur, wenn der Puffer Daten variabler Länge enthält, z. b. Zeichen-oder Binärdaten. Wenn der Puffer Daten fester Länge enthält, z. b. eine ganze Zahl oder eine Datums Struktur, ignoriert der Treiber die Länge des Daten Puffers und geht davon aus, dass der Puffer groß genug ist, um die Daten zu speichern. Das heißt, es werden niemals Daten fester Länge abgeschnitten. Daher ist es wichtig, dass die Anwendung einen ausreichend großen Puffer für Daten mit fester Länge zuweist.  
  
 Wenn eine Kürzung von nicht-Datenausgabe Zeichenfolgen auftritt (z. b. der für **SQLGetCursorName**zurückgegebene Cursor Name), ist die zurückgegebene Länge im Puffer Längenargument die maximal mögliche Zeichen Länge.  
  
 Für Eingabepuffer sind keine Datenpuffer Längen erforderlich, da der Treiber nicht in diese Puffer schreibt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verwenden von Längen-/indikatorenwerten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Datenlänge, Pufferlänge und Abschneiden](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Zeichendaten und C-Zeichenfolgen](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
