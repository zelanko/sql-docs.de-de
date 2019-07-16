---
title: Länge des Datenpuffers | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40fe9d23f14d4a7af80fe31a418cccf7133b7252
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067418"
---
# <a name="data-buffer-length"></a>Datenpufferlänge
Die Anwendung übergibt die Bytelänge der Datenpuffer an den Treiber in einem Argument, mit dem Namen *Pufferlänge* oder einem ähnlichen Namen. Z. B. in den folgenden Aufruf von **SQLBindCol**, die Anwendung gibt die Länge der *ValuePtr* Puffer ( **"sizeof" (***ValuePtr***)** ):  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Ein Treiber gibt immer die Anzahl der Bytes, die nicht die Anzahl der Zeichen in den Puffer-Length-Argument von jeder Funktion zurück, die ein Argument für eine Ausgabe.  
  
 Puffer Datenlängen sind nur für den Ausgabepuffer erforderlich; der Treiber verwendet diese, um das Schreiben nach dem Ende des Puffers zu vermeiden. Allerdings überprüft der Treiber die Länge des Puffers Daten nur dann, wenn der Puffer-Daten variabler Länge, wie z. B. Zeichen- oder Binärdaten enthält. Wenn der Puffer fester Länge-Daten, z. B. eine ganze Zahl oder Datum-Struktur enthält, wird der Treiber ignoriert die Länge des Puffers und setzt voraus, dass der Puffer groß genug zum Speichern der Daten ist; d. h. schneidet nie Daten fester Länge. Es ist daher wichtig, für die Anwendung einen ausreichenden Puffer für Daten fester Länge zugewiesen werden.  
  
 Tritt beim Abschneiden von nicht-Zeichenfolgen auszugeben (z. B. der Name des Cursors für zurückgegeben **SQLGetCursorName**), die zurückgegebene Länge in Puffer-Length-Argument ist die maximale Zeichenlänge möglich.  
  
 Puffer Datenlängen sind nicht erforderlich, für den Eingabepuffer, da der Treiber nicht auf diese Puffer geschrieben wird.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Längenindikator/Werte verwenden](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Datenlänge, Pufferlänge und Abschneiden](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Zeichendaten und C-Zeichenfolgen](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
