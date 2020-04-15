---
title: Ausrichtung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- alignment issues [ODBC]
ms.assetid: 06a01e51-e7a5-495f-aa27-e304b0d005ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 205cc3ff95dd60db215150f46ae894fbb99bd9ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288605"
---
# <a name="alignment"></a>Ausrichtung
Die Ausrichtungsprobleme in einer ODBC-Anwendung unterscheiden sich im Allgemeinen nicht von denen in jeder anderen Anwendung. Das heißt, die meisten ODBC-Anwendungen haben nur wenige oder keine Probleme mit der Ausrichtung. Die Strafen für das Nicht-Anrichten von Adressen variieren mit der Hardware und dem Betriebssystem und können so gering wie eine geringfügige Leistungseinbußen oder so groß wie ein fataler Laufzeitfehler sein. Daher sollten ODBC-Anwendungen und insbesondere portable ODBC-Anwendungen darauf achten, die Daten richtig auszurichten.  
  
 Ein Beispiel dafür, wenn ODBC-Anwendungen Ausrichtungsprobleme auftreten, ist, wenn sie einen großen Speicherblock zuweisen und verschiedene Teile dieses Speichers an die Spalten in einem Resultset binden. Dies tritt am ehesten auf, wenn eine generische Anwendung die Form eines Resultsets zur Laufzeit bestimmen und den Arbeitsspeicher entsprechend zuweisen und binden muss.  
  
 Angenommen, eine Anwendung führt eine vom Benutzer eingegebene **SELECT-Anweisung** aus und ruft die Ergebnisse aus dieser Anweisung ab. Da die Form dieses Resultsets beim Schreiben des Programms nicht bekannt ist, muss die Anwendung den Typ jeder Spalte bestimmen, nachdem das Resultset erstellt wurde, und den Speicher entsprechend binden. Die einfachste Möglichkeit besteht darin, einen großen Speicherblock zuzuweisen und verschiedene Adressen in diesem Block an jede Spalte zu binden. Um auf die Daten in einer Spalte zuzugreifen, gibt die Anwendung den an diese Spalte gebundenen Speicher um.  
  
 Das folgende Diagramm zeigt ein Beispielergebnissatz und wie ein Speicherblock mithilfe des Standarddatentyps C für jeden SQL-Datentyp an ihn gebunden werden kann. Jedes "X" stellt ein einzelnes Byte Speicher dar. (In diesem Beispiel werden nur die Datenpuffer angezeigt, die an die Spalten gebunden sind. Dies geschieht aus Gründen der Einfachheit. Im eigentlichen Code müssen auch die Längen-/Indikatorpuffer ausgerichtet werden.)  
  
 ![Standardmäßige Bindung von C-Datentypen an SQL-Datentypen](../../../odbc/reference/develop-app/media/pr24.gif "pr24")  
  
 Unter der Annahme, dass die gebundenen Adressen im *Address-Array* gespeichert sind, verwendet die Anwendung die folgenden Ausdrücke, um auf den an jede Spalte gebundenen Speicher zuzugreifen:  
  
```  
(SQLCHAR *)       Address[0]  
(SQLSMALLINT *)   Address[1]  
(SQLINTEGER *)    Address[2]  
```  
  
 Beachten Sie, dass die Adressen, die an die zweite und dritte Spalte gebunden sind, mit ungeraden Bytes beginnen und dass die an die dritte Spalte gebundene Adresse nicht durch vier teilbar ist, was der Größe eines SDWORD entspricht. Auf einigen Computern wird dies kein Problem sein; auf andere, wird es eine leichte Leistungseinbußen verursachen; auf anderen, es wird ein fataler Laufzeitfehler verursachen. Eine bessere Lösung wäre, jede gebundene Adresse an ihrer natürlichen Ausrichtungsgrenze auszurichten. Unter der Annahme, dass dies 1 für ein UCHAR, 2 für ein SWORD und 4 für ein SDWORD ist, würde dies das in der folgenden Abbildung gezeigte Ergebnis ergeben, wobei ein "X" ein Byte des verwendeten Speichers und ein "O" ein Nichtverwendete des Speichers darstellt.  
  
 ![Bindung nach natürlichen Ausrichtungsgrenzen](../../../odbc/reference/develop-app/media/pr25.gif "pr25")  
  
 Diese Lösung verwendet zwar nicht den gesamten Arbeitsspeicher der Anwendung, tritt jedoch nicht auf Ausrichtungsprobleme auf. Leider bedarf es einer angemessenen Menge an Code, um diese Lösung zu implementieren, da jede Spalte individuell nach ihrem Typ ausgerichtet werden muss. Eine einfachere Lösung besteht darin, alle Spalten an der Größe der größten Ausrichtungsgrenze auszurichten, die im Beispiel in der folgenden Abbildung 4 ist.  
  
 ![Bindung nach größten Ausrichtungsgrenzen](../../../odbc/reference/develop-app/media/pr26.gif "pr26")  
  
 Obwohl diese Lösung größere Löcher hinterlässt, ist der Code, um sie zu implementieren, relativ einfach und schnell. In den meisten Fällen gleicht dies die Strafe aus, die im ungenutzten Speicher gezahlt wird. Ein Beispiel, das diese Methode verwendet, finden Sie unter [Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).
