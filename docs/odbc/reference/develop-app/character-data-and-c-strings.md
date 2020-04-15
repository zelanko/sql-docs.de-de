---
title: Zeichendaten und C-Zeichenfolgen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- data buffers [ODBC], character data
- buffers [ODBC], C strings
- buffers [ODBC], character data
- character data and buffers [ODBC]
- length of data buffers [ODBC]
- data buffers [ODBC], C strings
- buffers [ODBC], length
- C strings and buffers [ODBC]
ms.assetid: 3a141cb4-229d-4027-9349-615cb2995e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7bb25022d4e0c0559f2a8f77b89a4ba26aeba33a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307490"
---
# <a name="character-data-and-c-strings"></a>Zeichendaten und C-Zeichenfolgen
Eingabeparameter, die auf Zeichendaten variabler Länge verweisen (z. B. Spaltennamen, dynamische Parameter und Zeichenfolgenattributwerte), weisen einen zugeordneten Längenparameter auf. Wenn die Anwendung Zeichenfolgen mit dem NULL-Zeichen beendet, wie es in C typisch ist, stellt sie als Argument entweder die Länge in Bytes der Zeichenfolge (ohne null-Terminator) oder SQL_NTS (Null-Terminated String) bereit. Ein Argument für nicht-negative Länge gibt die tatsächliche Länge der zugeordneten Zeichenfolge an. Das Length-Argument kann 0 sein, um eine Zeichenfolge mit null Länge anzugeben, die sich von einem NULL-Wert unterscheidet. Der negative Wert SQL_NTS weist den Treiber an, die Länge der Zeichenfolge zu bestimmen, indem das Null-Beendigungszeichen gefunden wird.  
  
 Wenn Zeichendaten vom Treiber an die Anwendung zurückgegeben werden, muss der Treiber sie immer null beenden. Dadurch kann die Anwendung entscheiden, ob die Daten als Zeichenfolge oder als Zeichenarray verarbeitet werden sollen. Wenn der Anwendungspuffer nicht groß genug ist, um alle Zeichendaten zurückzugeben, wird er von der Treiberauf die Bytelänge des Puffers abzüglich der Anzahl der Bytes abgeschnitten, die für das NULL-Beendigungszeichen erforderlich sind, die abgeschnittenen Daten wird null beendet und im Puffer gespeichert. Daher müssen Anwendungen in Puffern, die zum Abrufen von Zeichendaten verwendet werden, immer zusätzlichen Speicherplatz für das Null-Beendigungszeichen zuweisen. Beispielsweise ist ein 51-Byte-Puffer erforderlich, um 50 Zeichen Daten abzurufen.  
  
 Sowohl die Anwendung als auch der Treiber müssen beim Senden oder Abrufen von Long-Zeichen-Daten in Teilen mit **SQLPutData** oder **SQLGetData**besondere Vorsicht walten lassen. Wenn die Daten als eine Reihe von null-terminierten Zeichenfolgen übergeben werden, müssen die NULL-Beendigungszeichen in diesen Zeichenfolgen entfernt werden, bevor die Daten wieder zusammengesetzt werden können.  
  
 Eine Reihe von ODBC-Programmierern haben Zeichendaten und C-Zeichenfolgen verwechselt. Dass dies geschehen ist, ist ein Artefakt der Verwendung der C-Sprache beim Definieren von ODBC-Funktionen. Wenn ein ODBC-Treiber oder eine andere Anwendung eine andere Sprache verwendet - denken Sie daran, dass ODBC sprachunabhängig ist - ist diese Verwechslung weniger wahrscheinlich.  
  
 Wenn C-Zeichenfolgen zum Aufnehmen von Zeichendaten verwendet werden, wird das Null-Beendigungszeichen nicht als Teil der Daten betrachtet und nicht als Teil seiner Bytelänge gezählt. Beispielsweise können die Zeichendaten "ABC" als C-Zeichenfolge "ABC"0" oder als Zeichenarray "A", "B", "C" gehalten werden. Die Bytelänge der Daten ist 3, unabhängig davon, ob sie als Zeichenfolge oder Zeichenarray behandelt werden.  
  
 Obwohl Anwendungen und Treiber häufig C-Zeichenfolgen (null-terminierte Arrays von Zeichen) verwenden, um Zeichendaten zu halten, ist dies nicht erforderlich. In C können Zeichendaten auch als Array von Zeichen (ohne Null-Beendigung) behandelt werden, und seine Bytelänge wird separat im Längen-/Indikatorpuffer übergeben.  
  
 Da Zeichendaten in einem Array ohne Null-Termin gehalten werden können und seine Bytelänge separat übergeben wird, ist es möglich, Nullzeichen in Zeichendaten einzubetten. Das Verhalten von ODBC-Funktionen ist in diesem Fall jedoch nicht definiert und es ist treiberspezifisch, ob ein Treiber dies korrekt handhabt. Daher sollten interoperable Anwendungen immer Zeichendaten behandeln, die eingebettete Nullzeichen als Binärdaten enthalten können.
