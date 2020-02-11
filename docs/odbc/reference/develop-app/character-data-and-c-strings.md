---
title: Zeichendaten und C-Zeichen folgen | Microsoft-Dokumentation
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
ms.openlocfilehash: ed99ab72e3d5112588a0b1c93df34b01aff7acdd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68044922"
---
# <a name="character-data-and-c-strings"></a>Zeichendaten und C-Zeichenfolgen
Eingabeparameter, die auf Zeichendaten variabler Länge (z. b. Spaltennamen, dynamische Parameter und Zeichen folgen Attributwerte) verweisen, verfügen über einen zugeordneten length-Parameter. Wenn die Anwendung Zeichen folgen mit dem NULL-Zeichen beendet, wie es in C typisch ist, stellt Sie als Argument entweder die Länge in Bytes der Zeichenfolge (ohne das NULL-Terminator) oder SQL_NTS (NULL-terminierte Zeichenfolge) bereit. Ein nicht negatives Längenargument gibt die tatsächliche Länge der zugeordneten Zeichenfolge an. Das length-Argument kann 0 sein, um eine Zeichenfolge der Länge 0 (null) anzugeben, die sich von einem NULL-Wert unterscheidet. Der negative Wert SQL_NTS weist den Treiber an, die Länge der Zeichenfolge zu bestimmen, indem das NULL-Terminierungs Zeichen gesucht wird.  
  
 Wenn Zeichendaten vom Treiber an die Anwendung zurückgegeben werden, muss der Treiber ihn immer mit NULL beenden. Dies gibt der Anwendung die Wahl, ob die Daten als Zeichenfolge oder als Zeichen Array behandelt werden sollen. Wenn der Anwendungs Puffer nicht groß genug ist, um alle Zeichendaten zurückzugeben, verkürzt der Treiber ihn auf die Byte Länge des Puffers, abzüglich der Anzahl der Bytes, die für das NULL-Terminierungs Zeichen erforderlich sind, Null-beendet die abgeschnittene Daten und speichert Sie im ert. Daher müssen Anwendungen in Puffern, die zum Abrufen von Zeichendaten verwendet werden, immer zusätzlichen Speicherplatz für das NULL-Beendigungs Zeichen zuordnen. Beispielsweise ist ein 51-Byte-Puffer erforderlich, um 50 Zeichen von Daten abzurufen.  
  
 Beim Senden oder Abrufen von Long-Zeichendaten in Teilen mit **SQLPutData** oder **SQLGetData**muss sowohl von der Anwendung als auch vom Treiber besonders sorgfältig vorgegangen werden. Wenn die Daten als eine Reihe von null-terminierten Zeichen folgen weitergegeben werden, müssen die NULL-Beendigungs Zeichen in diesen Zeichen folgen entfernt werden, bevor die Daten erneut zusammengefügt werden können.  
  
 Eine Reihe von ODBC-Programmierern haben verwirrenden Zeichendaten und C-Zeichen folgen. Dabei handelt es sich um ein Element der Verwendung der Programmiersprache C beim Definieren von ODBC-Funktionen. Wenn ein ODBC-Treiber oder eine Anwendung eine andere Sprache verwendet, denken Sie daran, dass ODBC sprachunabhängig ist. diese Verwirrung ist weniger wahrscheinlich.  
  
 Wenn C-Zeichen folgen zum Speichern von Zeichendaten verwendet werden, wird das NULL-Terminierungs Zeichen nicht als Teil der Daten betrachtet und nicht als Teil der Byte Länge gezählt. Die Zeichendaten "ABC" können z. b. als C-Zeichenfolge "abc\0" oder als Zeichen Array {"A", "B", "C"} gehalten werden. Die Byte Länge der Daten beträgt 3, unabhängig davon, ob Sie als Zeichenfolge oder als Zeichen Array behandelt werden.  
  
 Obwohl Anwendungen und Treiber häufig C-Zeichen folgen (auf NULL endende Zeichen Arrays) zum Speichern von Zeichendaten verwenden, ist dies nicht zwingend erforderlich. In C können Zeichendaten auch als Zeichen Array behandelt werden (ohne NULL-Beendigung), und die zugehörige Byte Länge wird separat im Längen-/Indikatorpuffer übermittelt.  
  
 Da Zeichendaten in einem Array gespeichert werden können, das keine NULL-Werte hat, und die zugehörige Byte Länge separat übermittelt wird, ist es möglich, NULL-Zeichen in Zeichendaten einzubetten. Das Verhalten von ODBC-Funktionen ist in diesem Fall jedoch nicht definiert, und es ist Treiber spezifisch, ob ein Treiber dies ordnungsgemäß verarbeitet. Daher sollten interoperable Anwendungen immer Zeichendaten verarbeiten, die eingebettete NULL-Zeichen als binäre Daten enthalten können.
