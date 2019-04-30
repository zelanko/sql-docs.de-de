---
title: Zeichen, Daten und C-Zeichenfolgen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00daac655f0c435c1ee22239d3d4aafa23065997
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63217787"
---
# <a name="character-data-and-c-strings"></a>Zeichendaten und C-Zeichenfolgen
Eingabeparameter, die in Zeichendaten mit variabler Länge (z. B. Spaltennamen, dynamische Parameter und zeichenfolgenattributwerten) finden Sie haben einen zugeordnete Length-Parameter. Wenn die Anwendung die Zeichenfolgen mit Null-Zeichen wie üblich in C beendet wird, wird als Argument entweder die Länge in Bytes der Zeichenfolge (mit der Null-Terminator) oder SQL_NTS (Null-Terminated Zeichenfolge). Eine nicht Negative Length-Argument gibt an, die tatsächliche Länge der Zeichenfolge zugeordnet werden. Das Längenargument möglicherweise 0, um eine Zeichenfolge der Länge 0 (null), geben Sie die von einer NULL-Wert unterscheidet. Der negative Wert SQL_NTS weist den Treiber die Länge der Zeichenfolge zu bestimmen, indem Sie die Null-Terminierungszeichen suchen.  
  
 Wenn Zeichendaten vom Treiber auf die Anwendung zurückgegeben werden, muss der Treiber immer Null beendet werden. Dadurch wird der Anwendung die Entscheidung, ob die Daten als Zeichenfolge oder ein Array von Zeichen behandelt. Ist die Anwendungspuffer nicht groß genug für alle Zeichendaten zurück, der Treiber der Byte-Länge des Puffers minus der Anzahl der Bytes, die erforderlich sind, durch das Null-Abschlusszeichen schneidet, Null-terminiert die abgeschnittenen Daten und speichert ihn in das Puffer. Daher müssen Anwendungen immer zusätzlichen Speicherplatz für die Null-Terminierungszeichen in Puffern, die zum Abrufen von Zeichendaten verwendet belegt werden. Beispielsweise ist ein 51-Byte-Puffer zum Abrufen von 50 Zeichen, der Daten erforderlich.  
  
 Besondere Vorsicht durch die Anwendung und der Treiber beim Senden oder Abrufen von long-Zeichendaten in Teilen mit **SQLPutData** oder **SQLGetData**. Wenn die Daten als eine Reihe von Null-terminierte Zeichenfolgen übergeben werden, müssen die Zeichen Null-Terminierung an diesen Zeichenfolgen entfernt werden, bevor die Daten wieder zusammengesetzt werden können.  
  
 Eine Anzahl von ODBC-Programmierer haben Zeichendaten und C-Zeichenfolgen verwechselt werden. Ein Artefakt mit der Programmiersprache C, bei der Definition der ODBC-Funktionen ist dieses Problem aufgetreten ist. Bedenken Sie ein ODBC-Treiber oder eine Anwendung eine andere Sprache verwendet – sollten, dass ODBC sprachunabhängig ist – diese Verwirrung ist weniger wahrscheinlich auftreten.  
  
 Wenn C-Zeichenfolgen verwendet werden, um Zeichendaten zu speichern, wird der Null-Terminierungszeichen ist nicht als Teil der Daten und zählt nicht als Teil der Bytelänge. Beispielsweise kann Zeichen Daten "ABC" als die C-Zeichenfolge "ABC\0" oder das Array von Zeichen {"A", "B", "C"} gespeichert werden. Die Bytelänge der Daten ist 3, unabhängig davon, ob es als eine Zeichenfolge oder ein Array von Zeichen behandelt wird.  
  
 Anwendungen und Treiber häufig C-Zeichenfolgen (Arrays von Zeichen Null-terminiert) verwenden, um Zeichendaten enthalten, zwar gibt es nicht zwingend vorgeschrieben. In C können Daten auch als ein Array von Zeichen (ohne Null-Terminierung vorliegt) und die Byte-Länge, die separat übergeben werden, in den Längen-/Indikatorpuffer behandelt werden.  
  
 Da Zeichendaten in einer nicht-Null endendes Array gespeichert werden können, und die Bytelänge separat übergeben, ist es möglich, Einbetten von Null-Zeichen in der Zeichendaten enthalten sind. Allerdings in diesem Fall ist das Verhalten der ODBC-Funktionen nicht definiert und kann treiberspezifische gibt an, ob ein Treiber dies korrekt behandelt. Interoperable Anwendungen ausführen können sollte daher immer Zeichendaten behandelt, die eingebettete Null-Zeichen als binäre Daten enthalten kann.
